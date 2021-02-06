---
layout: post
title:  "Code Coverage - The metric that can make your tests worse"
permalink: /code_coverage/
tags: Code-Coverage Testing
---

There are a lot of issues with code coverage: Eloquently summed up by Stackoverflow.com user [Mark Simpson](https://stackoverflow.com/questions/695811/pitfalls-of-code-coverage/695888#695888):

> Code coverage tells you what you definitely haven’t tested, not what you have.

Just like with other metrics, there are ways to misuse it. In this article, I will not list all the flaws with it (you can Google them later). Instead, I will focus on one practice that caught my attention and that I am encountering more and more lately: **Setting a static code coverage target**.

Teams sometimes calculate code coverage during the build and add a check that fails it when coverage drops below a predetermined threshold. This is usually done to ensure that a newly written code is sufficiently tested.

But what should this predetermined threshold be?
Considering that not all code needs to be tested ([Kent Beck agrees on that](https://stackoverflow.com/questions/153234/how-deep-are-your-unit-tests/153565#153565)), having a threshold of 100% is not reasonable. Obvious examples for code that does not usually need to be tested are data transfer objects (DTOs) and automatically generated code.

<blockquote style="font-size: 1.4rem; margin: revert">
What a reasonable amount of code coverage is depends on your code and your application!
</blockquote>

### How can setting a static code coverage threshold make my tests worse then?!
Since you are reading this article about code coverage, I assume you know the importance of a reasonable test suite. Therefore you want to actually write all the necessary tests while developing.

The problem occurs when a **static** code coverage threshold is set, independent of your specific code base, possibly even by someone outside the development team. The intentions are usually good. The threshold should encourage you to write tests.

However, as mentioned above, what a reasonable code coverage is depends on your code. And your code base is different from some other teams. It also changes with every commit. Having a static threshold set by people outside the team is unlikely to be the exact threshold you would have come up with when reasonably approaching this.


This can lead to two possible situations:
> Your coverage is **above** that static threshold.

or
> Your coverage is **below** that static threshold.

<br>

Let’s have a look at these two situations:

<br>

### Case 1: Your coverage is above the threshold
At first sight, this seems like a great situation. Everybody is happy and the goal is achieved! What could possibly be wrong about this?

Let’s a little deeper into this though:

In this situation, when continuing the development, **at best** the developers simply ignore that threshold, they continue to write tests as usual and the whole threshold (and its integration into the build process) adds nothing to the development process.

What it also does is it suggests that a reasonable amount of code coverage has been reached to the people who set this threshold. While the truth is that the threshold simply might be too low to be any kind of useful indicator and therefore giving a false sense of security.

The **worst impact** this low threshold and it’s false sense of security has is the following:

Developers simply stop writing tests because “The coverage is already high enough”.

This is the **exact opposite** of what the people setting the threshold try to achieve with this undertaking.

<br>

### Case 2: Your coverage is below the Threshold

Keeping in mind that you know the importance of a reasonable test suite and actually **want** to write all the necessary tests. Let’s have a look at the **second situation** where the actual coverage is **below** that arbitrary threshold, even though you have written all the reasonable tests.
I can think of two possible options you have to still reach the threshold.

1. Excluding new code from the coverage report.
2. Writing more tests.

**Option 1:** Excluding code from the coverage report:
This option is only applicable when you are in control over the coverage runner.

Some code coverage runners allow the user to exclude certain parts of the code so they are not counted towards the overall coverage result.

Many of these runners, however, only allow whole files/packages to be excluded. Given that a class might have code that needs to be tested and also code that does not need to be tested you may end up unintentionally excluding code that you actually should test. An example for this could be a class with custom logic and an auto-generated `hashCode()` function. The coverage report will, in this case, not call out when there is untested code in that file/package.

This is again the exact opposite of what the person who set up the threshold tries to achieve.

**Option 2:** Writing more tests:

As mentioned above, I assume you value a sufficient test suit and you already wrote all the tests you considered reasonable. But when you now still need to increase your code coverage to reach that threshold, the only thing left is writing unreasonable tests.

This simply is a waste of time, effort and money and surely not what the people who set up the threshold in the first place had in mind.

At the end it boils down to **Goodhart’s law**, which states:
> When a measure becomes a target, it ceases to be a good measure.

If you feel that not enough code is covered by tests, I’d suggest, rather than imposing (potentially) counterproductive measures like a static code coverage threshold, enable your team.
Focus your effort on developer training about tests — you’ll get it back manifold when your colleagues understand the real benefits of a reasonable test suite.

### Summary:
- Code coverage threshold needs to be refined “organically”.
- The ideal amount of coverage depends on your code base and changes with every commit.
- If you have a static threshold instead: You might end up wasting time by writing useless tests, or stop writing tests that are actually necessary.


-----

<br>

### Addendum: How I personally use code coverage
The way I personally use code coverage is by running a build script with a test suite and coverage report after I finished a story. After running it, I check the coverage report to see if I might have missed testing something. If this is the case I then go back to the code and decide whether a test needs to be written here or not.
To be precise, I look at branch coverage as it can be more indicative of the comprehensiveness of a test suit compared to line coverage.

To be honest, I trust computers' memory more than my own memory, and that’s why my build script does, in fact, have a code coverage threshold that fails the build if I missed out on tests. So, even if I forget to check the coverage report and I did miss the threshold, I have a gentle reminder that I have to check if another test is necessary.

The important part is that the threshold is not static!

**Since I am in control over the threshold I can adjust that threshold when I realize it’s failing the build but another test would be unreasonable.**

**Additionally, I also  adjust the threshold when my changes increase the overall coverage. This is so that I don’t miss a reminder on future commits when necessary.**

I try to keep the threshold as close as possible to the actual coverage.

