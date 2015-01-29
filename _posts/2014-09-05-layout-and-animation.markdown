---
layout: post
title:  "Layout and Animation"
date:   2014-09-05 02:24:54
categories: update
---

Layout and Animation
-----------------------------

or: Its time to make your page awesome


Show and hide
-----------------------------

- Lazy man's animation
- Will show/hide the selected elements
- By writing "slow" or "fast" as an argument to the method, will animate the show/hide

Using show and hide
-----------------------------

{% highlight javascript %}
$("#myDiv").show("slow");

$("#myDiv").click(function() {
	$(this).hide("fast");
})
{% endhighlight %}


Animation
------------------------------

**Animation can make all the difference**

- Animation can make a page feel **alive**
	- Movement lets the user know the page is still ticking
	- We tend to associate momement with tought
		- "It reacted to me, so there must be 'something' behind it"
- Keeps the user engaged
- Generally enjoyable

12 Princples of animation
------------------------------

1. Squash and stretch
2. Anticipation
3. Staging
4. Straight ahead action and pose to pose
5. Follow through and overlapping action
6. Slow in and slow out
7. Arcs
8. Secondary action
9. Timing
10. Exaggeration
11. Solid drawing
12. Appeal

12 Principles as they apply to UIs
------------------------------

**Squash and stretch**

- Not used often, but can add an extra dimension to your UI elements
- Very *cartoony*

**Anticipation**

- It doesn't make sense for a UI element to move around without warning
- Making the element 'bounce' a bit in the opposite direction can provide a subtle cue
- Too much bounce can also become quite cartoony

**Follow through an overlapping action**

- Can be very slick
- Don't have everything move at once
- Have related elements move with a bit of a delay between each
	- Like hair, or a chain, or a whip
- Don't have them stop dead either
	- They might overshoot their target and need to settle back
	- Again, be careful not to be *too bouncy*


**Slow in, slow out**

- Called **easing** in the tech world
- **Crtically important** 
	- Easing is what will give all your transitions 'life'
- Subtle effect that pays off

** Arcs **

- Can be used when you want a more 'natural' motion in your UI
- Not strictly needed, can sometimes be distracting

**Secondary action**

- Often used in the *build in* process of a web page
- Have multiple elements all moving at the same time, emphasizing that the page is loading

**Timing**

- Used in UIs less to create a sense of weight, more to create a sense of *mood*
- Less time = faster = more energetic, high imporantance
- More time = slower = Mellow, refined, less jarring for the user

Communication / Location
------------------------------

- Users of your applications / pages will always be **navigating** your page's 'space'
- Just like real life where we navigate cities, rooms, hallways
	- In real life we can get a 'sense' of where we are by what moves where as we walk about
- We can communicate similar ideas by how items move about our page during usage
	- [Xbox UI Video](http://www.youtube.com/watch?v=F9rNh6-RybU)


Actually Animating
------------------------------

- "ENOUGH THEORY"
	- Is what you would yell if you had no self-control
	- But you do

jQuery Animation
-------------------------------

- is acceptable
- Can animate most css properties that have a *numerical value* associated with them


**EXAMPLE**

{% highlight javascript %}
$( "#book" ).animate(
	//properties to animate to
	{
		opacity: 0.25,
		left: "+=50"
	}, 
	//duration
	5000, 
	function() {
		// Animation complete.
	}
);
{% endhighlight %}

 In the example above

 - The animation will take 5000 miliseconds, or **five seconds**
 - The opacity will be at .25 at the end of the animation.
 - The book element will be 50 pixels further to the right.


 Setting DOM elements to be moved
 --------------------------------------

 - In order to move divs in the x/y direction, they need to be positioned either:
 	- **Absolutely**
 	- **Relatively**

 - Any div can be positioned **relatively** and still keep its normal DOM position
 	- Any divs positioned aboslutely with a relative div will set their top left positions based off the top left of the relative
 		- Yes, I know that's confusing, but it is also the truth


Rollover, Rollout effects
---------------------------------------

**Markup**

{% highlight html %}
<ul id="nav">
	<li>Un</li>
	<li>Deux</li>
	<li>Trois</li>
<ul>
{% endhighlight %}

**CSS**

{% highlight javascript %}
#nav li {
	position: relative
}
{% endhighlight %}

**Script**

{% highlight javascript %}
$("#nav li")
	.mouseover(function() {
		$(this).animate(
			{
				opacity: 1,
				top: "+=50"
			},
			700
		);
	})
	.mouseout(function() {
		$(this).animate(
			{
				opacity: .5,
				top: "-=50"
			},
			700
		);
	})
{% endhighlight %}


Build in
-----------------------------

- A very common use of animation
- Load in UI elements over time

**Example build in of the previous navigation**

{% highlight javascript %}
$("#nav li").each(function(index) {
	$(this)
		.delay(i * 200)
		.css("opacity", 0)
		.animate(
			{
				opacity: 1
			},
			700
		);
})
{% endhighlight %}


Velocity
---------------------------------

- A javascript library built for animation
- Get it at [http://julian.com/research/velocity/](http://julian.com/research/velocity/)
- Include velocity.min.js
	- AFTER jQuery
- Can tween everything jQuery does, and a few things more
- Typically faster than jquery's animate function

{% highlight javascript %}
$("#something").velocity({ opacity: 0.5, x: 10, y: 20 });
{% endhighlight %}


- Can also tween transforms

{% highlight javascript %}
$("#something").velocity({ rotation:30, scaleX:0.8 });
{% endhighlight %}


Tweenlite button rollovers
------------------------------------

**Markup**

{% highlight html %}
<div id="divHolder">
	<div id="testDiv">This is a test... div</div>
</div>
{% endhighlight %}

**CSS**

{% highlight css %}
#testDiv {
	position: absolute;
}

#divHolder {
	position: relative;
	margin: 20px 0 0 20px;
}
{% endhighlight %}

**Code**

{% highlight html %}
    <script src="bower_components/jquery/dist/jquery.min.js"></script>
    <script src="bower_components/velocity/velocity.min.js"></script>
    <script src="bower_components/velocity/velocity.ui.min.js"></script>
<script>
	$(document).ready(function() {
		$("#testDiv").mouseover(function() {
			$(this).velocity({ opacity: 1, scaleX: 1.2, scaleY: 1.2});
		}).mouseout(function() {
			$(this).velocity({ opacity: 0, scaleX: 1, scaleY: 1});
		})
	})
</script>
{% endhighlight %}


Principles (Google Material Design)
------------------------------------------

(Solid introduction to the basics)[http://www.google.com/design/spec/material-design/introduction.html]