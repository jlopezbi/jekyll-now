---
layout: post
title: First Evolved Shape, Hairball
date: 2017-01-10 01:22:18.000000000 -08:00
type: post
published: true
status: publish
categories:
- art
- generative
- programming
tags:
- blender
- deap
- evolution
- genetic programming
- plantGrower
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
<p>The first shape has been grown using an evolved program! This is part of the <a href="https://github.com/jlopezbi/PlantGrower">plant grower project</a> I am working on. It doesn't really look like much, but that's because it is evolved to grow as many nodes as possible in a set amount of time. So it is not surprising that it looks like a dense hairball. I suspect that results will get more visually interesting when the fitness criteria encourages compromise. Here is the shape:</p>

![hairball]({{ site.baseurl }}/images/hairball.png)

<p>The shape is really a representation of the 'phenotype.' A phenotype is 'the set of observable characteristics of an individual resulting from the interaction of its genotype with the environment.' (according to google) The genotype is below:</p>

![hairball_genome]({{ site.baseurl }}/images/hairball_genome.png)

<p>Rather simple, and it is plausible that a human could create such a program. All this program does is take the mean vector between x and x's unit vector. X is the vector describing the position of a collided sphere-'nutrient' relative to the node that just 'fed.' What is interesting is that this program was <em>evolved </em>rather than written by a human (me).  This evolution ran for five generations, where the population consisted of  ten individuals. The evolution is being run using <a href="http://deap.readthedocs.io/en/master/index.html">deap</a>. As far as genetic programming goes this is a small population and not many generations to get an interesting result (usually defined in terms of 'fitness'). But I am just working out the errors first with a simple prototype. For reference this point in the project has been git tagged as</p>

```fist-evolved-shape```

<p class="p1">looks like I was too much in a rush to type 'first'! Not sure what fist-evolving is :)</p>
