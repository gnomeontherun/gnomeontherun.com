---
layout:     post
title:      Using TypeScript with Angular Part 3 - IDE Support
subtitle:   TypeScript makes a better developer experience
date:       2015-10-29
header-img: img/typescript-bg.jpg
---

[TypeScript](typescriptlang.org) converts the source code to JavaScript so it can execute in the browser. Let's take a look at how TypeScript improves your IDE and development experience. This is Part 3 of a series covering TypeScript and Angular 1 & 2.

## TypeScript Development Experience

Perhaps my favorite feature that TypeScript powers is built in IDE and editor support. When writing JavaScript today, an IDE might be able to inspect an object and suggest certain things during editing. However, this is typically limited to letting you know about what properties and methods are available.

With TypeScript, we have more depth to things like autocomplete and linting. With types, we can also verify if incorrect values are passed, and your editor can warn you long before you try to run the application. The autocomplete can provide you with the value type a particular property contains, what types of values a method accepts, and what types a method returns.

Many JavaScript developers have lived without types, and question the value of this additional piece of information. To be fair, well documented code and using something like doc blocks can also make your editor aware of similar details. However, I rarely see doc blocks with typing information and you also don't get the value of a linting system on top. While I'm editing, I can import an Angular 2 item and autocomplete provides a full list of methods, properties with typing details.

While this is my opinion, adding TypeScript to your project is a way to establish an additional level of context for your code when someone else tries to read it. It can act like a contract between code blocks about what is allowed and in what way it should be used, thus helping reduce cognitive learning required to use the code and reduce the errors.

## Adding TypeScript to your editor/IDE

I use Atom, and the [atom-typescript](https://atom.io/packages/atom-typescript) package is the best  option. I can't recommend it enough.

If you use [Code](http://code.visualstudio.com/) TypeScript is built in. No plugins or configuration are required.

[WebStorm](https://www.jetbrains.com/webstorm/) provides [TypeScript support](https://www.jetbrains.com/webstorm/help/typescript-support.html), which can be setup with a few plugins and configuration options enabled.

For those [SublimeText]() users, Microsoft has a built a [plugin for you](https://github.com/Microsoft/TypeScript-Sublime-Plugin).

A few other options are listed at the [Typescript](http://www.typescriptlang.org/) site.

## TypeScript Series

* [Using TypeScript with Angular Part 1: Stronger Typing]({% post_url 2015/2015-09-07-using-typescript-with-angular-part-1-stronger-typing %})
* [Using TypeScript with Angular Part 2: ES6 and Transpiling]({% post_url 2015/2015-10-12-using-typescript-with-angular-part-2-es6-and-transpiling %})
