---
title: Independent Labs part 1 - Authentication & Authorization
date: "2019-07-05T22:40:32.169Z"
description: Independent Labs - People Engagement App
---

## Why

Last year, I conducted an engagement survey for a consulting client. This involved survey construction, survey administration, data collection, data analysis and interpretation so the executive team could make personnel decisions.

Making sense of the data was a challenge.

People in organizations vary in their comfort with statistical data. While I enjoy discussing the fundamentals of correlation and regression, I realized we needed _better tools_ to visualize the data.

Coming off Labs, I want to do an _independent_ Labs so I can build a survey data visualization tool. This will help me refine skills and build a portfolio piece that's connected to the work i'm doing.

## Progress So Far

#### Authentication

The first thing I worked on was setting up Authentiation via ![Auth0](https://auth0.com/). I'm using **implicit flow** and **universal login** for the App. Users will be directed to Auth0 for sign-in; they'll receive an identity token upon sign-in; then they'll be re-directed back to a callback URL that I've setup. Universal login is hosted by Auth0, with security benefits from having a single centralized login.

Basic login for the App
![Basic Login](./temp-login.png)

Auth0 Universal login
![Universal Login](./universal-log.png)

To make sure Authentication is working, I distinguish Public vs Private APIs; with the latter, login is required to access. To demonstrate, I created two server endpoints - a public & private endpoint.

```
app.get("/public", function(req, res) {
  res.json({
    message: "Hello from a public API!"
  });
});

app.get("/private", checkJwt, function(req, res) {
  res.json({
    message: "Hello from a private API!"
  });
});

```

You'll notice with a "private" endpoint, there's a function - checkJwt that checks for the user's access and id token:

```
const checkJwt = jwt({
  // Dynamically provide a signing key based on the kid in the header
  // and the signing keys provided by the JWKS endpoint.
  secret: jwksRsa.expressJwtSecret({
    cache: true, // cache the signing key
    rateLimit: true,
    jwksRequestsPerMinute: 5, // prevent attackers from requesting more than 5 per minute
    jwksUri: `https://${
      process.env.REACT_APP_AUTH0_DOMAIN
    }/.well-known/jwks.json`
  }),

  // Validate the audience and the issuer.
  audience: process.env.REACT_APP_AUTH0_AUDIENCE,
  issuer: `https://${process.env.REACT_APP_AUTH0_DOMAIN}/`,

  // This must match the algorithm selected in the Auth0 dashboard under your app's advanced settings under the OAuth tab
  algorithms: ["RS256"]
});
```

#### Authorization

Engagement surveys provide organizations with a wealth of data and information. The problem is, not everyone needs _all_ the data at once. As a department manager, I might want only data _specific_ to my department.

However, as a senior executive, I might want data for _all_ departments so I can see how different managers are doing relative to each other, allowing me to see which manager/department I may need to support.

This requires the app to have **authorization** where different levels of access is given depending on your role within the organization.

To keep things simple, I'm implementing Authorization via Roles. This requires setting up a new rule in Auth0:

![Authorization](./Authorization-roles.png)

Here I'm adding "roles to accessTokens", then I create a function to check for Role and an API endpoint that requires the "admin" role:

```
function checkRole(role) {
  return function(req, res, next) {
    const assignedRoles = req.user["http://localhost:3000/roles"];
    if (Array.isArray(assignedRoles) && assignedRoles.includes(role)) {
      return next();
    } else {
      return res.status(401).send("Insufficient role");
    }
  };
}

app.get("/admin", checkJwt, checkRole("admin"), function(req, res) {
  res.json({
    message: "Hello from a ADMIN API!"
  });
});

```

This means to access certain information, I'd have to login as "admin", otherwise the data won't be queried.

For the time being, the "admin" role is tied to any of my @gmail account logins, all other email accounts is given a "user" role.

![Admin Role](./admin-role.png)

For the time being, I can distinguish between admin vs user. At more advanced levels, I'd like each department to have their role role assignment (i.e., say in a global organization you have departments for SEAsia, China, US, EU or traditional departments like finance, marketing, operations, logistics etc).

For this, I'd transition to Access List Control, or I could go in to Auth0 and create additional rules.
