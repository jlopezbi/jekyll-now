---
layout: post
title: More Randomly Generated Growth Rules
date: 2016-12-21 01:35:58.000000000 -08:00
type: post
published: true
status: publish
categories:
- art
- generative
- programming
tags:
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
<p>Here are some more plant-shapes that are 'grown' in the same simulation environment, but with different randomly generated growth rules.  Note the variety in shapes! See the <a href="http://joshlopezbinder.com/randomly-generated-growth-rules/">previous post </a>for a detailed explanation. I am posting the most interesting structures I have come across, but many of the randomly generated rules result in 'boring' shapes, like a vertical line. Beware my aesthetic bias!</p>
<p>Since the last post I realized why many of the structures grew preferentially in a certain direction. This was because of the primitive functions 'add,' 'multiply,' and 'subtract' that operated element-wise on two vectors. Such element-wise operations are likely two take two vectors and make all there elements more positive, or more negative, or some combination. Because this affects the y-vector of the next node, this has a positive-feedback effect, resulting in structures that grew in one direction. I removed those functions for now.</p>
<p><strong>gnarly-spindly-tree </strong>Below is a structure tagged gnarly-spindly-tree (I am using git tags to keep track of interesting structures along the way.) Kinda reminds me of a blue-oak (Quercus douglasii)</p>
<p>This node-edge shape could be thought of as the 'phenotype' in the context of the evolutionary algorithm.</p>
<p><a href="http://joshlopezbinder.com/wp-content/uploads/2016/12/Screen-Shot-2016-12-20-at-4.17.47-PM.png"><img class="alignnone size-large wp-image-646" src="{{ site.baseurl }}/assets/Screen-Shot-2016-12-20-at-4.17.47-PM-785x444.png" alt="" width="785" height="444" /></a></p>
<p>Below is the full processor tree for the above structure. This can be thought of as the 'genotype.'</p>
<p><a href="http://joshlopezbinder.com/wp-content/uploads/2016/12/gnarly-spindly-tree.jpg"><img class="alignnone size-large wp-image-647" src="{{ site.baseurl }}/assets/gnarly-spindly-tree-785x125.jpg" alt="" width="785" height="125" /></a></p>
<p>Here is a close up of the processor tree 'genotype.'</p>
<p><a href="http://joshlopezbinder.com/wp-content/uploads/2016/12/gnarly-spindly-tree_close_up.jpg"><img class="alignnone size-large wp-image-648" src="{{ site.baseurl }}/assets/gnarly-spindly-tree_close_up-785x324.jpg" alt="" width="785" height="324" /></a></p>
<p>I have added some more primitive functions since the last post, like cross product for vectors, extracting the x, y, z component, and finding the angle between vectors.</p>
<p>Here are some more fun shapes!</p>
<p><strong>shagy-wild-bush</strong>. For this one the processor tree is so huge its not very informative to look at.</p>
<p><a href="http://joshlopezbinder.com/wp-content/uploads/2016/12/Screen-Shot-2016-12-20-at-4.36.45-PM.png"><img class="alignnone size-large wp-image-649" src="{{ site.baseurl }}/assets/Screen-Shot-2016-12-20-at-4.36.45-PM-785x443.png" alt="" width="785" height="443" /></a></p>
<p><strong>straight-segment-bush </strong>I like how simple this processor tree is, but still leads to an interesting growth shape. I probably would not have come up with this myself. Since the processor tree is simple enough to evaluate yourself, I'll explain its parts: x and y are vectors (<a href="http://joshlopezbinder.com/randomly-generated-growth-rules/">see prev. post for description of what they are)</a>. Norm( vec ) outputs the length of the input vector. Rotate_vec_np( vec1, vec2, angle ) rotates the first vector about the second vector, by some angle in radians (c1=.5 in this case). If_greater( arg1, arg2, arg3, arg4 ) outputs arg3 if arg1 is greater than arg 2, otherwise it returns arg4. Thats it!</p>
<p><a href="http://joshlopezbinder.com/wp-content/uploads/2016/12/Screen-Shot-2016-12-19-at-2.27.05-PM.png"><img class="alignnone size-large wp-image-650" src="{{ site.baseurl }}/assets/Screen-Shot-2016-12-19-at-2.27.05-PM-785x491.png" alt="" width="785" height="491" /></a></p>
<p><strong>No-Name </strong>Alas, the below structure was generated before I created a system for saving and 'resurrecting' processor trees.</p>
<p><a href="http://joshlopezbinder.com/wp-content/uploads/2016/12/Screen-Shot-2016-12-19-at-10.45.18-AM.png"><img class="alignnone size-large wp-image-651" src="{{ site.baseurl }}/assets/Screen-Shot-2016-12-19-at-10.45.18-AM-785x491.png" alt="" width="785" height="491" /></a></p>
<p><strong>A note on how I save the processor trees: </strong>I mentioned above that I am using a git tag to save out interesting shapes. In the past when working on generative projects like <a href="http://joshlopezbinder.com/works/coralsimulation/">this coral one</a>,  I tried to save out lists of parameters with a given shape. The problem with this is that as soon as I changed the code and added new parameters or completely different behavior, those parameter lists were useless! This time around I realized that that the entire code base of the project at the time the form is generated is the 'DNA' of a given shape. So really the best way to save that information is using <a href="https://en.wikipedia.org/wiki/Git">git</a>, a version control system for keeping track of code. I started the practice of committing all relevant code after an interesting shape was found, and then immediately using  ' git tag some-descriptive-name ' to associate that tag with a certain shape. That worked well until I started messing around with the randomly generated programs I have been referring to as 'processor trees.' To save these I have the script save a .txt file which contains a text representation of the processor tree. For example straight-segment-bush uses this processor tree:</p>
<p>if_greater(norm(x), norm(y), rotate_vec_np(x, y, c1), y)</p>
<p>If the structure is one I want to save, I copy the file and rename it, and I create a git tag of the same name. That way if I change the primitive set of functions that the processor tree uses, I can still go back to the version of the code where the primitive set was correctly configured for that processor tree. In this case I use</p>
<p class="p1"><span class="s1">git checkout refs/tags/tag-name</span></p>
<p>To re-enstate the code. Finally, there is a <a href="http://deap.readthedocs.io/en/master/api/gp.html#deap.gp.PrimitiveTree">function in the deap.gp library</a> that can recreate the working processor tree from the text-based representation. That's how I can resurrect an extinct virtual organism!</p>
