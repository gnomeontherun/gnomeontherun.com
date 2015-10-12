---
layout: post
date: 2015-10-12
title: "Using TypeScript with Angular Part 2: ES6 and Transpiling"
categories: javascript angular
read_time : 6
feature_image: categories/work-feature
show_related_posts: false
---

[TypeScript](typescriptlang.org) converts the source code to JavaScript so it can execute in the browser. Let's take a look at how TypeScript . This is Part 2 of a series covering TypeScript and Angular 1 & 2.

## TypeScript for ES6

TypeScript is a superset of ES6, which means TypeScript adds to the syntax of ES6 in order to provide the _strict typing_ we covered in [Part 1](/2015/09/using-typescript-with-angular-part-1-stronger-typing). All of ES6 is valid TypeScript, and means you are able to write your code however you like and still use TypeScript.

> TypeScript transpiles ES6 into vanilla ES5/3 JavaScript, even if you don't use TypeScript features.

That means features like modules, classes, arrow functions, and other ES6 features can be used and TypeScript will convert them into an equivalent ES5/3 syntax. You can use TypeScript as an ES6 transpiler even if you don't use TypeScript features, because it can still parse your source code and understand how to transpile it.

For Angular, this means you can use just TypeScript instead of another tool like Babel for transpiling ES6. Some features of Babel are opt-in, such as module loading, so with TypeScript you may get those features directly.

## How TypeScript transpiles to JavaScript

TypeScript is a NodeJS module, and can be used from the terminal. When TypeScript transpiles the source, it will inspect the code for any possible errors that can arise from using an incorrect value based on the typing information provided. For example, if you declare `let items:Array = []` and try to use it like `items.id = 'abc'` it will stop transpiling and show you the error that items is expected to be an array.

If the code passes the type validation, then TypeScript will remove any typing information from the code. Then it can run the resulting code through a parser that converts the content into the declared version of JavaScript, and downgrades the syntax to equivalent version.

## Coming up in future posts

* Angular 2 is also written in TypeScript, which means anytime you use an Angular 2 feature TypeScript will know if you are passing the correct types of values.
* TypeScript enhances IDEs since they can inspect the source and understand more about the expectations of code, and suggest to you what values are acceptable.
