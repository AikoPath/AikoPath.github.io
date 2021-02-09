---
layout: post
title:  "Analysing IMDB TV series data aka How Wesley Crusher affects Star Trek episode ratings"
permalink: /imdb-episode-ranking-star-trek/
tags: IMDB Python Star-Trek Data
date: 10-02-2020
---


Have you ever wondered how much influence a single actor has on the rating of a TV show’s episodes? This article will showcase you that you can analyse data from the internet movie database(IMDb) for this, using Star Trek The Next Generation as example series.

Some time ago I found out that my partner had not yet watched Star Trek The Next Generation(or any Star Trek series for that mater 😱). **I was excited for her!** She was going to experience something that anyone of us can only experience once in a life time: watching TNG for the first time! I was also a little bit excited for myself since it meant I could watch TNG again!

Some episodes into the first season I had noticed two things:

**First:**
Riker without a beard is just not the real Riker!

![Riker with and without Beard](/assets/img/imdb-episode-ranking-star-trek/riker.jpeg "Riker with and without Beard")

**And Second:**
I realized how annoyed I get when Wesley Crusher (played by Wil Wheaton) showed up.

I brought this second topic up with my partner, and explained how I think he is just an arrogant little brat. Surprisingly, my partner disagreed with me! And according to her “Wesley is cute”!

Now, even though I felt strongly about this, I know better than simply arguing back and forth about this matter (of taste?). Especially because I didn’t want to ruin TNG watching experience.

**Instead I turned to Science!**

Data Science to be exact.
(well... It's not really data science, I'm simply plotting some numbers and calculated some averages, please don't take this post too serious.)

After a short search I found IMDbPy, a python package to retrieve data from IMDb. I hacked in [a couple of lines of code](https://github.com/AikoPath/imdb_guest_actor_rating/blob/master/Star_trek_episode_comparison_by_cast.ipynb)¹ and ta-da!

[![Wil Wheaton](/assets/img/imdb-episode-ranking-star-trek/wil_wheaton.png "Wil Wheaton")](/assets/img/imdb-episode-ranking-star-trek/wil_wheaton.png)

I calculated the average episode rating of all episodes, as well as the average episode ratings for episodes with Wesely Crusher and without him. I also plotted all the episodes ratings for good measure.

As a result:

> I could show my partner proof that episodes with Wesely Crusher’s appearance have on average a lower rating than episodes without him.

To be fair, this does not mean that Wesely Crusher’s appearance makes an episode bad.

There are a lot of other factors that influence this average episode rating. I already mentioned Rikers beard above, then there is S02E22 which (as seen in the plot) is an outlier related to the writer’s strike that year. And there are many other things related to this e.g. viewers building emotional bonds with the characters over the early seasons and so on.

As usual:
> **Correlation is not causation!**

Nevertheless I ran the same code for some other non-permanent characters as well.

For example Colm Meaney who plays **Chief O’Brien**.

[![Colm Meaney](/assets/img/imdb-episode-ranking-star-trek/colm_meaney.png "Colm Meaney")](/assets/img/imdb-episode-ranking-star-trek/colm_meaney.png)

And **Barclay** who is played by Dwight Schultz who, surprisingly for me, correlates with a relatively high episode rating.

[![Dwight Schultz](/assets/img/imdb-episode-ranking-star-trek/dwight_schultz.png "Dwight Schultz")](/assets/img/imdb-episode-ranking-star-trek/dwight_schultz.png)

I also extended [the code](https://github.com/AikoPath/imdb_guest_actor_rating/blob/master/Star_trek_episode_comparison_by_cast.ipynb) even further to support comparisons between two non-permanent actors in the same plot.

As an example you can see the plot for **Dr. Crusher**(Gates McFadden) and **Dr. Pulaski**(Diana Muldaur), which show a few interesting findings.

1. The writer strike episode which I mentioned above is coincidentally the only episode where both show up.

2. Unsurprisingly to most TNG fans (my partner excluded…🤷‍♂️), the average rating of episodes showing Dr. Pulaski is lower than the equivalent with Dr. Crusher.

3. There are exactly two episodes without any of the doctors and the average rating of these two is higher than the average of either of the doctors alone. This can however mostly be attributed to the excellent rating of Episode S02E16 “Q Who”

[![McFadden & Muldaur](/assets/img/imdb-episode-ranking-star-trek/mcfadden_muldaur.png "McFadden & Muldaur")](/assets/img/imdb-episode-ranking-star-trek/mcfadden_muldaur.png)

If you have ever watched The Next Generation you know that one of the most likeable characters of the series is **Q**, played by John de Lancie, he doesn’t appear often, but when he does you know you are in for a treat! Similar things can be said about the appearances of Whoopi Goldberg who played **Guinan**, the counseling bartender.


There are exactly two episodes where both of them show up and those are two outstanding episodes! The graph below shows each episode rating plotted as a bar, with a blue bar representing an episode with **Guinan**, a red bar is used for an episode with **Q**, and a green bar representing both appearing in that episode!

The average rating of the two episodes with actors reaches an incredible 8.8! John de Lancie’s appearances reach an impressive average of 8.0.

[![de Lancie & Goldberg](/assets/img/imdb-episode-ranking-star-trek/de_lancie_goldberg.png "de Lancie & Goldberg")](/assets/img/imdb-episode-ranking-star-trek/de_lancie_goldberg.png)

The full source code can be found [here](https://github.com/AikoPath/imdb_guest_actor_rating/blob/master/Star_trek_episode_comparison_by_cast.ipynb).

Next steps:

* There are a few next steps that can be done to get some more information out of this data:
* Look at episode description and find the general episode themes and see how they rank against each other. (eg. look for keywords like Borg, Cardassian, Worf etc. )
find all non-permanent cast automatically

¹: we all know that it’s not just a couple of lines of code, and it surely didn’t work on the first try but this is a blog post and you have no proof that I failed!
