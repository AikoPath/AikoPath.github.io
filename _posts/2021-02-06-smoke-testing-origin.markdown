---
layout: post
title:  "The origin of Smoke Testing and the confusion it can cause"
permalink: /smoke-testing-origin/
tags: Testing Smoke-Testing
---

You know what smoke testing is, right? Yes! Great, I also thought I knew, as did a colleague of mine. The problem: each of us had a different interpretation of the meaning.

As mentioned in my article, [visualization and prioritization of technical debt](https://aiko.dev/visualising-and-prioritizing-technical-debt/), analogies can significantly help with grasping abstract concepts. This is where a term like “Smoke Testing” can come in handy, as long as everyone involved has the same understanding of the analogy.

## The story

A colleague and I were discussing how to verify the functionality of our recent production deployment. He mentioned that we could do some manual smoke testing. This confused me a little bit since that’s not how I understood “smoke testing”.

Luckily for me, I knew the origin of the analogy, and I could derive what ‘’smoke testing’’ in software development means. So I started to explain why smoke testing has this name, and why his understanding was wrong.

## Hardware Smoke Testing

I pointed out that the term “smoke testing” originated from hardware development. If you power on a circuit board for the first time and you see smoke rising, you know it’s broken.

Therefore, I was arguing, that simply booting up the application and making sure that the application doesn’t immediately die, would be a sufficient smoke test. This could be done automatically as a step in the build pipeline. “Lessons Learned in Software Testing” by Cem Kaner, James Bach, Brett Pettichord describes the origin as follows:

<blockquote style="font-size: 1.4rem; margin: revert">
"The phrase smoke test comes from electronic hardware testing. You plug in a new board and turn on the power. If you see smoke coming from the board, turn off the power. You don’t have to do any more testing."
</blockquote>

## Smoke Testing in Plumbing

So far so good, right? I felt my explanation was sound and since it matched any uses of the term I had seen in software development, I had a valid reason to believe that this was the one and only explanation of the term and my colleague could do nothing but agree with me.

Boy, was I wrong!

Right after I finished my explanation, my colleague (who might or might not have been a plumber in a previous life) started sharing his understanding of the origin of smoke testing and it was a very different story.

In the plumbing industry, smoke testing is done to verify that a pipe is not leaking.

![Smoke coming out of tubes](/assets/img/smoke-testing-origin/smoke-new-york.jpg "Smoke coming out of tubes")

Smoke is created artificially, blown into tubing, and then the pipes are examined to make sure there is no smoke leaking.

Transferring this understanding to software development, therefore, meant that after the application start, multiple simple user flows are executed to ensure basic functionality. And he added, in his understanding, this was mostly done manually in contrast to a full and automated functional test suit.

## My mind was blown!

Not only did my colleague has a different story to tell about the origin of the term smoke testing but it all made sense as well. And I googled it – plumbers do actually do that and it is indeed called smoke testing.

## So, where did we go from there?

What we both agreed upon is that smoke testing:
* Tests basic functionality
* Is one of the first, if not the first test after deployment
* Provides fast feedback to see if further testing even makes sense

However, we were indifferent about what basic functionality meant in this context. So we looked around for what other people had to say about “smoke testing”. We found multiple definitions and the lines between these definitions were foggy (pun intended).

So we finally agreed on something that made sense to us in our situation and went with that for the duration of the project.

## Conclusion

* What smoke testing really means for you depends on your team. Whatever meaning you chose does not matter, just make sure that everyone on your team has the same understanding.

* When talking about it with people outside of your team be aware of different meanings and clarify first before it results in misunderstandings.

* Regardless of the terminology that you agree upon, smoke tests usually offer fast feedback to your development process and codebase.
