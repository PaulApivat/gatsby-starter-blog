---
title: Independent Labs - Material-UI Hooks vs HOC
date: "2019-07-06T22:40:32.169Z"
description: People Engagement App - Material-UI Hooks vs HOC
---

## Material-UI

Material-UI is user interface framework, built specifically out of React components. This makes it suitable for a React application in that anything you grab from Material-UI is a _pre-built_ React component.

That includes buttons, toolbars, navigation menus, icons and much more.

I had just started using Material-UI for our labs project and I wanted to continue using this framework to dive deeper.

### New Features for Material-UI Components

Since the last time I used Material-UI, just a month and a half ago, they've made a subtle change to their component setup. Instead of higher order components (HOC), they've switched to using Hooks.

I quickly ran into issues when I tried creating a basic login button for the App.

A comparison of two different styling approaches highlights the contrast:

**makeStyles(styles, [options]) => hook**

```
import React from "react";
import { makeStyles } from "@material-ui/core/styles";

const useStyles = makeStyles(theme => ({
    paper: {
        ...
    },
    form: {
        ...
    }
}))


const LoginHook = () => {
    const classes = useStyles();
    return(
        <Container>
            <form>
                ...
            </form>
        </Container>
    )
}

export default LoginHook;
```

**withStyles(styles, [options]) => higher-order component**

```
import React from "react";
import { withStyles } from '@material-ui/styles';

const styles = {
    paper: {
        ...
    },
    form: {
        ...
    }
}

class LoginHOC extends React.Component {
    render(){
        const { classes } = this.props;
        const { login } = this.props.auth;    <---- login function passed down as props>
        return(
            <Container>
                <form>
                    ...
                </form>
            </Container>
        )
    }
}

export default withStyles(styles)(LoginHOC);
```

Hooks and HOC are very similar except for one crucial difference, Hooks are structured as functional components, while HOC allow for class components. In the case of my Login component, I needed to structure it as a **class** component because the login function that is tied to the **Auth0** authentication I have setup in Auth/Auth.js needs to be passed down to the Login component, so it needs to accept the `login` function as props.

This way, the sign-in button can trigger the universal login with Auth0.

Nevertheless, because it is expected that everyone is moving towards Hooks, I will have to switch to hooks. Before doing that, I'll make sure to pass all Auth/Auth.js functions down via React Context.

Then switch over all components to Hooks. This is something planned post-MVP.
