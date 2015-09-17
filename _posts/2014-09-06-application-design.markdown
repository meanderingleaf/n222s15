---
layout: post
title:  "Application Design"
date:   2014-09-06 02:24:54
categories: update
---

Application Design
-----------------------------

An app is not a site
-----------------------------

Apps lack (by default)
-----------------------------

- Transitions
- Pages
- State
- Links

These are all distinct things
----------------------------

- A link is not a page.
- Nor is a transition a link itself

But they are also all related
-----------------------------

- They need a way to communicate with each other
- How does a link know when to navigate to another page.
- How does the page know to play the transition?


Enter the application
-----------------------------

- object that links the pieces together


Application responsibilities
--------------------------------

- Creating the different components of the application
- Putting those components into their correct place
- (typically) storing the data that the application will use throughout
- Enabling communication between the separate components
- Changing what is visible to the user at runtime


Creating the components
-------------------------------

- First lines of code in an application, might be done in a constructor/init function


Placing the components
--------------------------------

- Will either select objects on the DOM an attach events and data
- Or create new objects at runtime and place them into the DOM (typically in placeholders)


Communication Between Components
-----------------------------------

- Acts as the mailer
- Gets messages from one component, makes sure they move to others
- Can also make values accessible to all components via something called **application state**

Storing data / Application State
---------------------------------

- Later on applications will have data that will be loaded into the highest level, to be referenced by other objects  in the program

Finite State Machines
--------------------------------

- Many applications act as Finite State Machines
- Essentially, what this means is that they only will be in one 'state' (or page) at a time
- To move from page to page, a transition must be manually triggered.
- The change from page to page is typically accomplished via a transition function
