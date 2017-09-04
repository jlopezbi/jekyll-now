---
layout: post
title: Getting DEAP (or any python module) into Blender
date: 2016-12-07 19:02:39.000000000 -08:00
type: post
published: true
status: publish
categories:
- ideas
- programming
tags:
- blender
- deap
- python
meta:
  _edit_last: '1'
author:
  login: jlopezbi
  email: joshlobinder@gmail.com
  display_name: jlopezbi
  first_name: Joshua
  last_name: Lopez-Binder
---
<p><code></code>In my quest to make lots of different interesting shapes, I am attempting to use <a href="http://deap.readthedocs.io/en/master/">DEAP</a> inside of blender. Deap stands for Distributed Evolutionary Algorithms in Python. Deap has a module for implementing <a href="http://www.macs.hw.ac.uk/~ml355/common/thesis/c6.html">genetic programming</a>, which I am curious and excited to use as a way of automatically generating growth rules.  Genetic programming evolves computer programs to perform some sort of task well. I am not really sure, at the moment, if it is important that the growing tree-structures perform some task well. However, the deap package includes an interface for easily generating random programs from a collection of predefined 'primitves' or basic functions. It also allows one to easily construct a <a href="https://en.wikipedia.org/wiki/Genetic_algorithm">genetic algorithm</a> which uses the randomly generated programs as 'genomes.'  Anyway, first I need to make the deap package available within blender!</p>

<p>1. Blender's most current versions use python 3. Deap is written in python 2. So to covert I used the <a href="https://docs.python.org/2/library/2to3.html">command 2to3</a> as follows (note I am on OSX):</p>

```
$ 2to3 --output-dir=/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/deap -W -n /Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/deap
```

<p class="p1">2. The next step is to get blender's version of python to be aware of deap. The quickest way I found to do this is to add the location of the python 3.5 site-packeges to blender's path. This is done according to this <a href="https://www.blender.org/forum/viewtopic.php?t=21528">thread</a>. In blender's console I did this:</p>

```
>>> sys.path.append('/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/
>>> import deap.gp
```

<p class="p1">It works! Of course this a bit of a hacky way of getting deap (or any third-party python module) into blender. More permanent ways of making the module available for import are described <a href="http://blender.stackexchange.com/questions/5287/using-3rd-party-python-modules">here</a>.</p>


