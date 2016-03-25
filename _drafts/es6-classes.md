## ES6 Class Series

ES6 classes provide a new syntax for creating objects and their prototypes. This syntax appears more familiar to developers from other backgrounds, such as Java, and traditional JavaScript developers might view it as odd or unnatural. ES6 classes are not like classes in other programming languages like Java, they still are objects (like almost everything in JavaScript).

There have been a lot of advocates and opponents of classes in JavaScript. The promise of classes is best thought of as a way to more cleanly standardize the way objects are defined. The primary criticisms about classes are not around its syntax, but rather that it provides no new features and lends itself to misconceptions about what is actually happening.

In a course of several posts, we'll dig into the syntax and semantics around classes, and you can decide for yourself if you support or reject its use. Several modern JavaScript frameworks (Angular 2, Ember) leverage the class syntax as the preferred method of declaring objects, so it should be worth understanding clearly.

**Chapter Contents**

* TL;DR;
  * Class Syntax
  * Constructor
  * Properties
  * Methods
* Class Syntax
  * Class declarations
  * Class expressions
  * `this`
  * Strict mode
* Class Methods
  * Constructor method
  * Prototype methods
  * Static methods
* Subclassing
  * Extending a class
  * Calling parent with super
  * Mix-ins
  * Limits

## Class Syntax

In this post we'll look at the syntax and semantics of a class. Before we look at the `class` syntax, let's look at some common ways to construct an object using ES5.

    ES5 CODE SAMPLES

You can see in these samples, the result always creates an object with properties and methods stored on the prototype. These are still valid ways to create objects, but let's look at the same result using an ES6 class.

```
class Percent {
  static format(number) {
    return number / 100;
  }
}
```

## Class Static Methods

A static method is a method that can be called without instantiating the class object. You most likely have used static methods like `Math.round()` or `localStorage.getItem()`.

To declare a static method, use the keyword `static` before the method name.

```
class MathExtra {
  static randomBetween(min = 0, max = Number.MAX_SAFE_INTEGER) {
    return Math.floor(Math.random() * (max - min + 1) + min);
  }
}

var num = MathExtra.randomBetween(10, 100); // Yields a random number between 10 and 100
```

Static methods are only available on the class object, not on any instances. So if you tried to do `var me = new MathExtra(); me.randomBetween(0, 10);` it would throw a `Uncaught TypeError` because the static method is not part of the instance prototype. 
