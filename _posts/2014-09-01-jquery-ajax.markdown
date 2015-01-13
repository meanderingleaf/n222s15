---
layout: post
title:  "JQuery and AJAX"
date:   2014-09-02 03:24:54
categories: update
---


JQuery and AJAX
-------------------------

Javascript Libraries
-------------------------

Writing plain JS can be troublesome

	- Inconsistent implementation across browsers
	- Extremely long syntax
	- Several lines of code needed to accomplish easy tasks

Several JS libraries arose to deal with these issues

	- MooTools
	- Scriptaculous
	- jQuery
	- Yahoo User Interface tools (YUIs)

jQuery
--------------------------

Becoming the defacto standard library

To the winner goes the spoils

	- jQuery will most likely be cached on the user’s machine
		- No performance hit to include in your site
		- ONLY IF you use a link to a jQuery the user has already downloaded
		- Using a CDN (content delivery network)

Lots of support for jQuery in the community

Tons of plugins developed

jQuery
-----------------------------

Is, fundamentally, a DOM manipulation javascript library. It provides the developer with a set of tools to select DOM elements, modify, add, and remove them.

Additionally it provides a developer with easy access to robust implementations of animations, event handling, and AJAX.

Getting jQUery
---------------------------------------

There's a number of ways to get jquery

1. Download the library at [http://jquery.com/](http://jquery.com/)

	- Download it an include it with your files
	- Typically stored in a folder called ‘js’ or ‘scripts’

2. Or, use the version hosted on google ajax libraries

	- Will load faster on user machines who have already visited a site that used this jQuery link
	- Will _not_ work if you do not have an internet connection and are developing on your local machine
	- 

3. Install using bower
	
	- On the commandline (make sure youre inside your project folder) `bower install jquery`
	- I'll be using this in class a lot

(For this class always download and include jQuery in your project)

Including jQuery
----------------------------------------

- Use the src attribute of the script tag
- Make sure to include jquery scripts before any of your other scripts
- Else you won’t be able to use jQuery (it won’t be loaded in yet)

{% highlight html %}
	<script src="js/jquery.min.js"></script>
{% endhighlight %}


**note** the location & name may change base on where you have put your jquery file.

Waiting until the page has fully loaded
--------------------------

It is common, when using jQuery, to wait until a page has fully loaded before running any selector code. This ensures that the the elements on the page that are you trying to select are actually selectable. The syntax for waiting for a page to load in jQuery looks like this:

{% highlight javascript %}
$( document ).ready(function() {
 	//its safe to write jquery selectors in here.
});
{% endhighlight %}


Almost all of our jquery code you will see contained inside of a document ready event handler.


jQuery: Selectors
--------------------------

jQuery works using css selectors

 - \# to select a DOM element with an ID
 - . To select a DOM element with a class

Can also use the generic class (“a” or “li”)

Can target nested objects with a space
	- \#myDiv .nav li
	- The above would select all the li elements inside of anything with a class of ‘nav’ inside of a div with id of ‘myDiv’


jQuery: Selecting
-------------------------------

{% highlight javascript %}
//select element with id=“myElement”
$(“#myElement”)

//selects all elements of class ‘nav’
$(“.nav”)

//selects all links
$(“a”)
{% endhighlight %}


jQuery: Changing HTML
-------------------------------

- Use the html method
- Will overwrite any other HTML in the element

{% highlight javascript %}
$(“#myDiv”).html(“Hello world!”);
{% endhighlight %}


jQuery: Adding elements
------------------------------

- Use appendElement
- Does not overwrite any existing content
- Adds content beneath all other content

{% highlight javascript %}

$(“#myDiv”).append(“<p>Hi there!</p>”;);

{% endhighlight %}


- using prepend
- Does not overwrite any existing content
- Adds content before all other content

{% highlight javascript %}

$(“#myDiv”).prepend(“<p>Hi there!</p>”;);

{% endhighlight %}


jQuery: Removing elements
--------------------------------

- Use the remove method

{% highlight javascript %}
//gets rid of any elements on the stage with a class of ‘badclass’
$(“.badClass”).remove();
{% endhighlight %}


jQuery: Changing CSS
--------------------------------

- Use the css method
- Can be used to get the current CSS value
- Or to set a new value

{% highlight javascript %}
//as a getter
$(“#myDiv”).css(“height”) //returns the height of the div

//as a setter
$(“#myDiv”).css(‘width’, 100);
$(“#myDiv”).css(‘backgroundColor’, ‘#FF0000’);
{% endhighlight %}


jQuery: Chaining
----------------------------------

- All methods in jQuery return a reference to the element (s) acted on
- This allows you to use multiple methods on one line (‘chaining’ methods)

{% highlight javascript %}
//this is valid
$(“myDiv”)
	.css(“width”, 100)
	.css(“height”, 100)
	.appendElement(“<p>Hello there!</p>”);
{% endhighlight %}


Responding to events
-----------------------------------

Jquery has built-in methods for most events

- Mouse over
- Mouse out
- Click
- Mouse down
- Mouse up
- Mouse move

**Responding to a click**

{% highlight javascript %}
$(“#someDivID”).click(function() {
	console.log(“The div has been clicked”);
})
{% endhighlight %}

**Responding to Over and Out**

{% highlight javascript %}
$(“#someDivId”)
	.mouseover(function() {
		console.log(“Mouseover”);
	})
	.mouseout(function() {
		console.log(“Mouseout”);
	})
{% endhighlight %}

**Responding to Just Mouseout**

{% highlight javascript %}
$(“.someClassName”).mouseout(function() {
	console.log(“Mouse has left an element with the class of someClassName”);
});
{% endhighlight %}


Caching Selected elements
-----------------------------------------

It is possible to store the selected elements in code for later reference. Here's one, dumb example.


{% highlight javascript %}

//get a ref to 'markedDiv'
var soonToBeDead = $("#markedDiv");

//that ref works like a selected jQuery object
soonToBeDead.click(function() {
	//remove soon to be dead from the DOM
	soonToBeDead.remove();
});
{% endhighlight %}


Caching selections are makes it easy to update your code (only have to change one selector if you give a div a new ID), and saves the computer some processing time (everytime you write `$()` the selector engine has to go out looking for whatever you specify it to look for which takes time).



AJAX
-----------------------------------------

Short for Asynchronous Javascript and XML

	- A method for loading in textual resource at runtime
	- Developed by Microsoft


AJAX
-------------------------------------------

A way of loading in new content for your application **at runtime**

	- XML
	- JSON
	- Entirely new pages
	- Lightboxes

Can send data along with the request as well

	- POST
	- GET

jQuery AJAX
---------------------------------------------

{% highlight javascript %}
$.get("example.txt", function(data) {
	console.log(data);
})
{% endhighlight %}

- Supply an object to the ajax function
- Specify URL to load
- Specify function to run if the load is a success


Inline functions
---------------------------------------------

This is the first time we have seen an inline function

	- Inline functions are ones that we define within another function’s context

Typically they do not have a name

You will see these a lot in javascript