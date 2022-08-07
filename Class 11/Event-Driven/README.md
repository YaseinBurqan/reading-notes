# Event-Driven

## Event-Driven Programming in Node.js

Event-Driven Programming is a logical pattern that we can choose to confine our programming within. In this article we'll go over how it works and how we can make the best use of it in our Node.js projects. The concept is rather ubiquitous and can be found in any major framework or software.

### Overview

Every time you interact with a web page, an event is happening. These events have associated functions that, when triggered, execute to make a change to the user interface. Examples of Event-Driven Programming can be found in The Web Browser and other high-level programming languages.

- Event-Driven Programming makes use of the following concepts:

    An Event Handler is a callback function that will be called when an event is triggered.
    A Main Loop listens for event triggers and calls the associated event handler for that event.

### EventEmitter

Node.js provides us with a useful module called EventEmitter that allows us to get started incorporating Event-Driven Programming in our project right away. There are several modules published on npm which promise a faster performance than the native eventEmitter for your project's code.

### Removing Listeners

Node allows you to remove event listeners from an event. This could be for performance reasons or to avoid memory leaks. To remove an event in EventEmitter you must pass a reference to the function you wish to remove. It is often best to name your event handling functions rather than leaving them anonymous.

### Object Oriented Programming + Event-Driven Programming

The Object Oriented approach promotes the idea that all behavior of an individual unit (or object) be handled from code within that unit. Using this approach, applications are built with many different units that all speak to and interact with each other. These two paradigms make for a very valuable combination in a wide variety of situations.

With Mailbox.sendMail we use the sendMail function to send and receive mail. This is a standard approach, but what if we later decide we want to log every time we send mail? We can make use of Event-driven programming to solve this problem.

#

## Events

## [Node.js v18.4.0 documentation](https://nodejs.org/api/events.html)
