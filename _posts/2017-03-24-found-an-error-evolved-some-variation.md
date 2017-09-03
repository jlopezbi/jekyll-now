---
layout: post
title: Simple Method more Valuable than Complex Tool
date: 2017-03-24 19:52:27.000000000 -07:00
type: post
published: true
status: publish
categories:
- generative
- programming
tags:
- evolution
- genetic programming
- learning
- python
- wip
meta:
  _edit_last: '1'
author:
  login: jlopezbi
  email: joshlobinder@gmail.com
  display_name: jlopezbi
  first_name: Joshua
  last_name: Lopez-Binder
---

![4_grid]({{ site.baseurl }}/images/target13_4_phenos.png)

<p><strong>Above:</strong> Phenotypes from 4 different runs of the same evolution. The goal was to reach a fixed target number of nodes in the colony, in this case 13. The genomes for each shape are sub-programs composed of primitive functions (see <a href="https://en.wikipedia.org/wiki/Genetic_programming">genetic programming</a>). This was possible because an important error was removed from the code. See below.</p>
<p><strong>Slow Evolutions</strong></p>
<p>Evolution runs prior to this post were excruciatingly slow. I attributed this, naively, to each growth simulation taking a long time.  I even made the simulation runs take half as long, by making the collision computation more efficient. But the evolution runs were still frustrating me. On some level I knew, perhaps intuitively, that they shouldn't be quite so slow. Individuals simulation runs were pretty quick. So it was frustrating and bewildering that the evolution took so long!</p>
<p><strong>Looking Under the Hood with Dots</strong></p>
<p>At this point I recalled a conversation with my friend Amiti, who is a software developer, about running scripts that take a long time. She mentioned that when dealing with these long computations, she's gotta see <em>something </em>happening, even if it is just printing out periods or dashes. So I had the evolution script print a "." each time it did a simulation run. At first I saw the dots appear quickly, like the pattering of rain in a puddle, but then the intervals got longer and longer. Each dot succeeded the next with increasing sluggishness! This definitely wasn't right. For a sanity check I added a timer and verified that the simulation runs got progressively longer during the course of an evolution.</p>
<p><strong>Memory Leaks</strong></p>
<p>From there it was pretty easy to deduce that some sort of <a href="https://en.wikipedia.org/wiki/Memory_leak">memory-leak</a> phenomena was occuring. Turns out I was re-using an instance of an object which 'grows' the colony. I switched the code to re-instantiate the object each time a simulation ran, and the problem went away. I'm not even sure exactly why this was happening, but for the time being <em>it doesn't matter</em>.<em> </em>The evolution runs are fast enough now to have a decent population (50-200) and have multiple simulation runs per genome. This is necessary since there is some random variation between each simulation run for the same genotype.</p>
<p><strong>The Lesson</strong></p>
<p>So lesson learned: <strong>The lowest cost change that gives any indication of what is going on is highly valuable.</strong> Printing dots was more helpful than a fancy tool like profiling, which led me down a bit of a rabbit hole trying to figure out how to use the tool. I am sure profiler's have their place for me, but only <em>after</em> the simpler methods have been exhausted.</p>
<p>&nbsp;</p>
