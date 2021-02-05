---
layout: post
title:  "Visualising and Prioritizing Technical Debt"
permalink: /visualising-and-prioritizing-technical-debt/
tags: Technical-Debt Prioritizing Project-Management
---

Whether we know it or not, we probably have technical debt in our codebase! And the longer we keep it, the more problems it creates. So let’s get rid of it. But where do we start?

[![Tech Debt and Business Value](/assets/img/visualising-and-prioritizing-technical-debt/tech_debt_business_value.jpeg "Tech Debt and Business Value")](/assets/img/visualising-and-prioritizing-technical-debt/tech_debt_business_value.jpeg)


## So, what is technical debt again?
Let’s have a look what Martin Fowler has to say about it:

> Technical Debt is a wonderful metaphor developed by Ward Cunningham to help us think about this problem. In this metaphor, doing things the quick and dirty way sets us up with a technical debt, which is similar to a financial debt. Like a financial debt, the technical debt incurs interest payments, which come in the form of the extra effort that we have to do in future development because of the quick and dirty design choice. We can choose to continue paying the interest, or we can pay down the principal by refactoring the quick and dirty design into the better design. Although it costs to pay down the principal, we gain by reduced interest payments in the future.

Here is the [full article](https://martinfowler.com/bliki/TechnicalDebt.html) for your reading pleasure.

At a given point in time, it might make sense for us to create some technical debt. After all, it will give us the freedom to focus on “more important” things to do right then. We sincerely agree that we will get rid of it once there is less work to do and we have more time at hand.

Making a conscious decision to add technical debt to our code base and commit to removing it later is just the first step though. The sad truth is: due to another upcoming deadline or just steadily incoming or changing requirements, we might not even think about the debt anymore.

Visualising the debt we have is a necessary step that needs to follow in order to keep it on our minds so we are aware of it and can tackle it before it gets out of hand.


[![Tech Debt Tattoo](/assets/img/visualising-and-prioritizing-technical-debt/todo_arm_tattoo.jpeg "Tech Debt Tattoo")](/assets/img/visualising-and-prioritizing-technical-debt/todo_arm_tattoo.jpeg)
Even though the method shown in the picture makes sure we won’t forget our technical debt, it is hard to find a volunteer.

Generally, some methods have advantages over others when it comes to remembering things.

Since we are all technologists, the first thing that comes to mind is storing it online, for all team members to access.

But let’s face it: having a virtual space to collect debt is just a way to get it off our mind. It would be hidden on some page in a project management tool that we would never look at again.

<blockquote style="font-size: 1.4rem; margin: revert">
This means we need a physical board showing our debt!
</blockquote>

Now that we are aware of our technical debt it’s time to get rid of it. But how do we prioritize it?

In the following we’ll be discovering two different ways of categorising and visualising technical debt that will make it easier for our team to prioritize and then decide where to focus our efforts.

## Technical Debt Matrix
(inspired by the [Eisenwhower Matrix](https://encrypted.google.com/search?q=eisenhower%20matrix)

Some types of technical debt are easy to remove and require only a small amount of effort. While other types are connected to many components of our system and require a large amount of effort to eliminate.

At the same time, removing some of the technical debt offers great value to our development process and the product we are working on, while some debt removals offer nothing at all.

Having a clear picture of these factors help a lot when it comes to prioritizing debt removal.

[![Tech Debt Matrix](/assets/img/visualising-and-prioritizing-technical-debt/tech_debt_matrix.jpeg "Tech Debt Matrix")](/assets/img/visualising-and-prioritizing-technical-debt/tech_debt_matrix.jpeg)


In the chart above the technical debt is arranged using the two criteria mentioned above and categorised into 4 quadrants.

In the future whenever we decide to create some new technical debt or discover new debt in our system, we simply take a sticky note (As an agile development team we should have them lying around everywhere), write a description of the tech debt on it, and place it on the chart according to the ease of removal and value it offers.

The lower left quadrant is where removing the tech debt is expensive and only offers little value. This contains tech debt we shouldn’t focus our initial effort on.

Better are the upper left and lower right quadrants. Here the removal is either easy or highly valuable, but respectively expensive or of little value.

The obvious winner here is the upper right quadrant. In fact, since the top right corner in most graphs is typically the "best" quadrant, we have consciously chosen the x-axis to be *ease* instead of *effort* to have this matrix better match the common experience.

Removing the technical debt located here is very valuable to our development process in addition to it also requiring only little effort to do so. Not only can we go for the low hanging fruit first but we also identified the most valuable ones. A classical win-win situation.

## Technical Debt Tree

The world of software development is full of metaphors to make concepts easy to grasp or just to give them a catchy name. We talk about Factory Pattern, Chaos Monkeys, Garbage Collection, we talk about how Viruses can infect our computers and how Firewalls can protect us from them. One of my favourite metaphors in software development is the Scouting Rule¹. Even Technical Debt itself is a metaphor.

So let’s bring this metaphorical thinking to our tech debt visualisation.

[![Tech Debt Tree](/assets/img/visualising-and-prioritizing-technical-debt/tech_debt_tree.jpeg "Tech Debt Tree")](/assets/img/visualising-and-prioritizing-technical-debt/tech_debt_tree.jpeg)

Continuing with the low hanging fruits metaphor: the sticky notes located at the lower end of the tree represent technical debt that can be solved easily; figuratively the low hanging fruits. The notes hanging higher on the tree are more difficult tasks and require more effort.

Now we have the same distinction between easy and hard to remove technical debt as with the quadrant representation above. What’s missing is the visualisation of how much value it offers.

Here’s where the sticky size comes into play. Just like picking a large apple from a tree gives you more nutritious value for your effort than picking a small one: The size of the notes represent the value of removing this piece of debt offers.

Additionally, the different sizes of the sticky notes give an insightful overall representation on how much technical debt there really is. The bigger the area covered with sticky notes is, the more your development is slowed down by the debt you have.

Independent of whether we enjoy a more analytical visualisation, or a more playful one we can now start including the removal of tech debt in our iteration planing.

## Summary

* Having a physical representation of your tech debt is important to not forget about it

* Categorizing the debt helps you prioritizing it correctly

* Focus on the technical debt which removal offers much value while at the same time does not take a lot of effort


¹: even though “**Boy** Scout Rule” is the more popular term I’m sure the [Girl Scouts](https://www.girlscouts.org/)) follow the same directive.
