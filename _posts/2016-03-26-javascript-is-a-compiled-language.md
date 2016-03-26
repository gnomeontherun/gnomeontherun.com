---
layout: post
date: 2016-03-26
title: "JavaScript is a compiled language"
categories: javascript
read_time : 5
feature_image: categories/work-feature
show_related_posts: false
---

With ES6 and the introduction of new language features on a yearly basis, the language is evolving at a rate that browsers currently cannot keep up. Today's JavaScript has a richer syntax to express new concepts or old concepts in new ways.

### However, tools (re)write our code

We rarely write the JavaScript that we ship to our users. Due to the constraints of writing and deploying modern JavaScript, today's JavaScript is fundamentally a compiled language. Perhaps better said, JavaScript is a "compile-to" language.

> JavaScript is a "compile-to" language.

I am lumping together both the idea of compilers like Babel or CoffeeScript, which take code and convert it into ES5 JavaScript, as well as optimization tools like minifiers, which rewrite code to reduce payload and attempt to algorithmically optimize the result.

The code that browsers actually load and execute is rarely the code that developers write themselves. For some time now, we've relied on tools that concatenate, minimize, and otherwise optimize our source code into something different for delivery. We trust these tools to correctly maintain the functionality we envisioned with our source code.

> We don't write the JavaScript code that browsers execute. We let tools render the final version of our code.

Due to the quality of the most popular compiler tools, this doesn't appear to have caused major issues in JavaScript. This means we need to pay close attention to the compilers we use and be active in helping improve and maintain their quality.
