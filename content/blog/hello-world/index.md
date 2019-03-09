---
title: Sprint Challenge - Labs 1 - Paul Apivat
date: "2015-05-01T22:12:03.284Z"
---

## Part 1 - Individual Accomplishments this Sprint
This past week, my primary task was to create a display page for our app, namely the Invoice List page and Create Invoice page. I was able to get a basic html structure up, section-tags and div-tags and I was able to do very basic CSS styling to put boundaries around the various sections of the page. 

I also got the functionality for the Create Invoice page to work. First, I got it so that all form input was stored on local state. Then, I re-did the whole thing to where ALL user data was stored in one data object, ready to be sent to the backend. 

In this regard, the challenge was creating sub, reusable, components sending props to the main form component so that form local "state" would store all invoice related data in one data object so it can be sent to the backend. 

Handling different data types and input fields was a challenge as it required importing many child components, passing props to child components, but having user data stored on the parent component. 

## Detailed Analysis



Oh, and here's a great quote from this Wikipedia on
[salted duck eggs](http://en.wikipedia.org/wiki/Salted_duck_egg).

> A salted duck egg is a Chinese preserved food product made by soaking duck
> eggs in brine, or packing each egg in damp, salted charcoal. In Asian
> supermarkets, these eggs are sometimes sold covered in a thick layer of salted
> charcoal paste. The eggs may also be sold with the salted paste removed,
> wrapped in plastic, and vacuum packed. From the salt curing process, the
> salted duck eggs have a briny aroma, a gelatin-like egg white and a
> firm-textured, round yolk that is bright orange-red in color.

![Chinese Salty Egg](./salty_egg.jpg)
