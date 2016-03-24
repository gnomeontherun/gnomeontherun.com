## ES6 Class Series

ES6 classes provide a new syntax for creating objects and their prototypes. This syntax appears more familiar to developers from other backgrounds, such as Java, and traditional JavaScript developers might view it as odd or unnatural. ES6 classes are not like classes in other programming languages like Java, they still are objects (like almost everything in JavaScript).

There have been a lot of advocates and opponents of classes in JavaScript. The promise of classes is best thought of as a way to more cleanly standardize the way objects are defined. The primary criticisms about classes are not around its syntax, but rather that it provides no new features and lends itself to misconceptions about what is actually happening.

In a course of several posts, we'll dig into the syntax and semantics around classes, and you can decide for yourself if you support or reject its use. Several modern JavaScript frameworks (Angular 2, Ember) leverage the class syntax as the preferred method of declaring objects, so it should be worth understanding clearly.



## ES6 Class Syntax

In this post we'll look at the syntax and semantics of a class. Before we look at the `class` syntax, let's look at some common ways to construct an object using ES5.

    ES5 CODE SAMPLES

You can see in these samples, the result always creates an object with properties and methods stored on the prototype. These are still valid ways to create objects, but let's look at the same result using an ES6 class.

    ES6 CODE SAMPLE
