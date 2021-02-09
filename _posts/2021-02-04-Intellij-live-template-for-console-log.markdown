---
layout: post
title:  "IntelliJ Live Template for console.log"
permalink: /intellij-live-template-for-console-log/
tags: IntelliJ console.log() JavaScript TypeScript
date: 09-08-2017
---

### A handy shortcut for one of our most common tasks

We’ve all been there. Our code is not behaving like we hoped it would and it’s not obvious why. The easiest and fastest way to get a clue for what’s going on is to simply put a print statement in the code. It’s not nice; we should use a proper debugger, but we do it anyway.

The following live template will
* add the `console.log(‘’)` statement to your code
* automatically insert the class name, function name, and line number in the log message
* offer code completion for the message you want to log
* and place the cursor where you need it.

According to [Larry Wall](http://threevirtues.com/), the original author of the Perl programming language, one of the three great virtues of a programmer is laziness.

**So let’s automate the boring stuff!**

Here’s a video showing the setup and usage of the live template. You can pause and skip parts of the video or just follow the instructions below.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UcWxT25DuCA" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

### Steps to Follow
Live template preferences:

* Go to Preferences( ⌘ + , ).
* Select Editor/Live Templates (you can type live templates to find it).
* Select Javascript.
* Press the ‘+’ sign in the top right corner of the window( ⌘ + N ).
* Select Live Template (press 1 or Enter).

Edit template:
* Enter the abbreviation you want to assign to the template. We will use `cl` in this case.
* Enter the description for the template (e.g. “inserts console.log(‘’);” ).
* Paste the following template code:

```
console.log('Class: $CLASS$, Function: $FUNCTION$, Line $LINE$ $PARAM_TEXT$($EXPECTED$): '
, $PARAM$);$END$
```

* Click Define below the template text field and select the contexts where this template should apply (e.g. JavaScript, Typescript, etc.)
* Edit variables (feel free to add or leave out template variables that you (don’t) need.):
* Click Edit Variables.
* Select ‘jsClassName()’, ‘jsMethodName()’, ‘lineNumber()’ as Expression to CLASS, FUNCTION, LINE respectively.
* Add ‘PARAM’ as a default Value of PARAM_TEXT.
* Check Skip if Defined for these variables.
* Order variables so that PARAM comes before PARAM_TEXT and EXPECTED.

Now go ahead type `cl` and press Enter (or Tab if that is your default). Tada! There is our template already with line number, class and function name and the cursor is waiting for you to type the second parameter which will instantly appear in the string of the log message. By pressing Enter, the cursor will jump to the next undefined parameter. Type something, press Enter again, and you are at the end of the line.

And there you have your log statement!

### Explanation
* $PARAM$ is the placeholder for the expression that you want to log.
* $PARAM_TEXT$ will be replaced with this expression due to the default value binding.
* $CLASS$, $FUNCTION$, $LINE$ will be replaced with the className, methodName, and lineNumber as specified.
* $END$ indicates the position where the cursor will be placed after every variable has been set.

The order of the variables is important since it defines the order where the cursor jumps to next after pressing Enter. Special in this case is that the cursor will skip PARAM_TEXT since it was defined through PARAM before.

The mechanics used here can be applied to many other use cases like a custom logger or other general language features. Some other useful expressions that can be assigned to template variables are `complete()` and `completeSmart()`, which lets you use autocomplete within strings.

I’d love to see your favourite use cases and examples in the comment section.
