---
layout: post
title:  "Typescript Rundown"
date:   2014-09-02 03:24:54
categories: update
---


Typescript Rundown
-------------------------


Goodness, its pretty much just javascript but let's make sure we're all okay with that.


Strings
-------------------------

```
var myName:string = "Professor X";
```

Numbers
--------------------------

```
var meaningOfLife:number = 42;
```

Arrays
---------------------------

They're typed now!

```
var toBuy:string[] = [ "Bananas", "Milk", "Whatever looks good"];
```

Booleans
----------------------------

```
var isIndianaWeatherOdd:bool = true;
```

Functions
----------------------------

Need to specify a return type now, and argument types

function greet(x: string, y: string): string {
    return x+y;
}