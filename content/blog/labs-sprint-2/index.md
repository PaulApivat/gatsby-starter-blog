---
title: Labs Sprint 2 Integration
date: "2019-03-25T22:40:32.169Z"
description: Sprint Challenge - Labs 2 - Integration.
---

Labs Sprint 2 Challenge. 

## Part 1 - Individual Accomplishment this Sprint

This past sprint, I worked primarily on getting our calendar feature ready and functional. When creating a new invoice, our Invoice App will allow our users to pick a current and due date for the invoice. The challenge for me was getting a React calendar component that would allow users to pick a date - and, this was the challenging part - having the dates picked be added to ONE data object when the user clicks "generate" in creating a new invoice. Finally, I was able to hook up a react-day-picker component to our application, allowing users to send up the data object as one object. 

The second challenge was communication-originated. When we were discussing our wireframe, it was very basic and only after starting to REALLY think about features and user experience did I realize we needed TWO separate calendar functions. One day picker and one for Google Calendar API - where we wanted the user to be able to add an "invoice due" event to their own personal (google) calendar. 

Figuring out how to use Google Calendar API within the context of how we wanted users to experience the application was a huge challenge. Google Calendar API is not the easiest to understand. I spent several days trying to read the documents and figuring things out. 

Most of my work this past sprint was in React. I had to translate Vanilla Javascript to React was another challenge. I ended up using the react-day-picker component and mixing and matching an implementation of accessing Google Calendar API on the frontend. 

![Calendar Day Picker](./react-day-picker.png)
 

Accomplishment:
- Successfully Implementing a Calendar using [React Day Picker](https://react-day-picker.js.org/)
- Successfully Implementing [Google Calendar API](https://developers.google.com/calendar/)

At the end of the day, we need to have two calendar functions, not one. That was a revelation for me. 


### Detailed Analysis

My most challenging ticket was implementing Google Calendar API.

I had to implement a user sign-in first, then that would lead to a button that, when clicked opened up the user's Google Calendar, with a ready made template ready for the user to enter event details into their calendar. 

The first button prompts users to log into their Google Account. Then once logged in, the second button opens a new popup window directly into a Calendar Event template. When the user fills out that calendar event, it gets added to their calendar, they can close out that popup window and get back to their create invoice form. 

![Google Signin Prompt](./google-signin.png)

![Google Calendar Event Template](./google-cal-template.png)


### Part 2 - Weekly Reflection

The Big Oxmox advised her not to do so, because there were thousands of bad
Commas, wild Question Marks and devious Semikoli, but the Little Blind Text
didn’t listen. She packed her seven versalia, put her initial into the belt and
made herself on the way.

1.  So baboon this
2.  Mounted militant weasel gregariously admonishingly straightly hey
3.  Dear foresaw hungry and much some overhung
4.  Rash opossum less because less some amid besides yikes jeepers frenetic
    impassive fruitlessly shut

When she reached the first hills of the Italic Mountains, she had a last view
back on the skyline of her hometown Bookmarksgrove, the headline of Alphabet
Village and the subline of her own road, the Line Lane. Pityful a rethoric
question ran over her cheek, then she continued her way. On her way she met a
copy.

> The copy warned the Little Blind Text, that where it came from it would have
> been rewritten a thousand times and everything that was left from its origin
> would be the word "and" and the Little Blind Text should turn around and
> return to its own, safe country.

But nothing the copy said could convince her and so it didn’t take long until a
few insidious Copy Writers ambushed her, made her drunk with Longe and Parole
and dragged her into their agency, where they abused her for their projects
again and again. And if she hasn’t been rewritten, then they are still using
her. Far far away, behind the word mountains, far from the countries Vokalia and
Consonantia, there live the blind texts.

#### Silent delightfully including because before one up barring chameleon

Separated they live in Bookmarksgrove right at the coast of the Semantics, a
large language ocean. A small river named Duden flows by their place and
supplies it with the necessary regelialia. It is a paradisematic country, in
which roasted parts of sentences fly into your mouth.

Even the all-powerful Pointing has no control about the blind texts it is an
almost unorthographic life One day however a small line of blind text by the
name of Lorem Ipsum decided to leave for the far World of Grammar. The Big Oxmox
advised her not to do so, because there were thousands of bad Commas, wild
Question Marks and devious Semikoli, but the Little Blind Text didn’t listen.

##### Wherever far wow thus a squirrel raccoon jeez jaguar this from along

She packed her seven versalia, put her initial into the belt and made herself on
the way. When she reached the first hills of the Italic Mountains, she had a
last view back on the skyline of her hometown Bookmarksgrove, the headline of
Alphabet Village and the subline of her own road, the Line Lane. Pityful a
rethoric question ran over her cheek, then she continued her way. On her way she
met a copy.

###### Slapped cozy a that lightheartedly and far

The copy warned the Little Blind Text, that where it came from it would have
been rewritten a thousand times and everything that was left from its origin
would be the word "and" and the Little Blind Text should turn around and return
to its own, safe country. But nothing the copy said could convince her and so it
didn’t take long until a few insidious Copy Writers ambushed her, made her drunk
with Longe and Parole and dragged her into their agency, where they abused her
for their projects again and again.