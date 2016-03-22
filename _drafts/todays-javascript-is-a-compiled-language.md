With ES6 and the introduction of new language features on a yearly basis, the language is evolving at a rate that browsers currently cannot keep up. Today's JavaScript is no longer the simple jQuery like code many developers grew up on. It has a richer syntax to express new concepts or old concepts in new ways.



We rarely write the JavaScript that we ship to our users. Due to the constraints of writing and deploying modern JavaScript, today's JavaScript is fundamentally a compiled language. Perhaps better said, it is a "compile-to" language.

### Tools (re)write our code

The code that browsers actually load and execute is rarely the code that developers write themselves. In fact, this has been true for quite some time.

CoffeeScript was the most popular metalanguage that compiled to JavaScript. There are many projects written with CoffeeScript, but browsers don't understand it and it requires compilation. As one would expect, there are also many flavors of CoffeeScript that tackle various quirks and features.

For some time now, we've relied on tools that concatenate, minimize, and otherwise optimize our source code into something different for delivery. We trust these tools to correctly maintain the functionality we envisioned with our source code.

> We don't write the JavaScript code that browsers execute. We let tools render the final version of our code.

There are certainly developers who write all their JavaScript and personally optimize it for delivery, but this doesn't scale or work in a larger team environment. JavaScript that is written for production is almost certainly preprocessed by some set of tools.

### Compile for backwards compatibility

Some browsers are close to supporting the features introduced into the language, but any web developer should be painfully aware that a large percentage of users are on older versions of browsers. For example, the ES6 arrow function feature is supported reasonably well across many desktop browsers (as of March 2016), but has no support for Safari on desktop or mobile (all the iDevices!).

We cannot write code with these new features and expect to support older (and even current) browsers. The solution is to let these tools do the hard work of algorithmically compiling our (hopefully) well considered source code into something all targeted browsers can understand.

### The benefits

### The drawbacks

### Compile forever?

I don't see a day anytime soon where JavaScript won't require some form of transformation. At a minimum, there will always be the need to do optimization steps (much like you should optimize your images). This doesn't worry me, in fact it
