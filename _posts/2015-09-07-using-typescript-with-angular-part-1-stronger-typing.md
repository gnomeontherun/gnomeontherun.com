---
layout: post
date: 2015-09-07
title: "Using TypeScript with Angular Part 1: Stronger Typing"
categories: javascript angular
read_time : 10
feature_image: categories/work-feature
show_related_posts: false
---

After giving a [talk on Angular 2](http://www.meetup.com/AngularJS/events/224748092/) recently, one big question I felt came up in different ways was: why TypeScript? I'd like to share some insights I have into why or why not [TypeScript](typescriptlang.org) is useful to Angular developers, regardless if you are using v1 or v2. This is Part 1 of a series covering TypeScript and Angular 1 & 2.

## TypeScript provides stronger typing for JavaScript

Most simply, TypeScript provides _stricter typing_ support for JavaScript. There already are [types in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures), such as a `Number`, `String` and `Boolean`, which makes JavaScript _loosely typed_ in nature. Another feature of JavaScript is that variables are not typed, only values. For example, in this statement we have a variable called `answer` which references a `Number` value of `42`.

    var answer = 42;

However, JavaScript doesn't care what you do with the `answer` variable later on. I can easily do this without any kind of problem.

    var answer = 42; // Set answer to a number value of 42
    answer += 'number'; // Concatenate a string value to a number value
    console.log(answer); // Outputs `42number` as a string

This is probably a bug you've come across at some point in your time working with JavaScript. We set the `answer` variable to a `Number` value, but over time it turned into a `String`. JavaScript _coerces_ variables over time, allowing a variable to change types over time. This can cause problems when you expect a variable to be a `Number` and you get a `String`.

> TypeScript provides a layer on top of JavaScript that _enforces_ types remain consistent.

TypeScript has the ability to inspect your code, and prevent you from writing the code from above. Instead, TypeScript would send an error at `answer += 'number';` saying `Type 'string' is not assignable to type 'number'`. So TypeScript enforces types where JavaScript does the best it can to execute your code through coercion.

## Interfaces for complex types

JavaScript has the `Object` type, which is a complex type that can have many properties. TypeScript provides the concept of an `Interface` which allows you to describe the structure of more complex objects easily. Take this code sample in JavaScript.

    var me = { // Declare the me variable with an object
      name: 'Jeremy'
    };
    if (me && me.name) { // Check the object and property exist before using
      console.log('Hello ' + me.name);
    }

This simple example shows that before using an object property you may need to check if it exists, and to do that you have to check if the object exists and then if the property exists on that object. Doing just `if (me.name)` could result in error if `me` is not defined. Essentially JavaScript only cares that something is an object, and not what properties exist or how they are described.

TypeScript interfaces can describe an object (or a function, or a class, or anything) in detail so those properties can also be _type enforced_. The above could be written in TypeScript like this.

    interface Person { // Declare an interface, to describe a complex object
      name: string // Give it a property of name, which is a string
    }
    var me:Person = { // Define the variable, and type it as a Person
      name: 'Jeremy'
    };
    console.log('Hello ' + me.name); // Use the property without fear

Here we don't have to write the `if` statement, because TypeScript will check the presence and type of the properties. Many lines of JavaScript written don't properly check if an object property exists before using it, causing many `undefined` errors.

## Coming up in future posts

There are many other features and ways to look at types. I'll go into more detail about several other features and use cases for TypeScript.

* TypeScript is an ES6 transpiler as well, allowing you to leverage ES6 features today. You might use it just for ES6 support.
* Angular 2 is also written in TypeScript, which means anytime you use an Angular 2 feature TypeScript will know if you are passing the correct types of values.
* TypeScript enhances IDEs since they can inspect the source and understand more about the expectations of code, and suggest to you what values are acceptable.
