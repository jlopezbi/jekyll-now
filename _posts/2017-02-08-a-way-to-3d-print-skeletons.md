---
layout: post
title: 'A Way to 3D Print Skeletons: Metaball Skinning'
date: 2017-02-08 06:13:40.000000000 -08:00
type: post
published: true
status: publish
categories:
- ideas
- programming
tags:
- 3dPrinting
- blender
- graphics
- python
- wire-frame
meta:
  _edit_last: '1'
author:
  login: jlopezbi
  email: joshlobinder@gmail.com
  display_name: jlopezbi
  first_name: Joshua
  last_name: Lopez-Binder
---
<p><strong>Metaball Skinner:</strong> Update (Mar 24, 2017): I made this functionality into a blender add-on! Get it here: <a href="https://www.blendermarket.com/products/metaball-skinner" target="_blank">https://www.blendermarket.com/products/metaball-skinner</a></p>

![asdf]({{ site.baseurl }}/images/monkeys_compare.png)
*Left: result from metaball skinning script I wrote. This model is guaranteed to result in a valid mesh for 3d printing. Right: Built in skin modifier (blender) with a subdivision surface smoothing. This model is likely to cause errors when processed for 3d printing.*


<p>In the midst of working on <a href="https://github.com/jlopezbi/PlantGrower">evolving plant/coral thingmabobs</a>, I am exploring 3d printing some of the earlier shapes I came up with, when I was writing the growth algorithms explicitly. To do this I need a reliable way to 'skin' the skeletons (or 'thicken' the wireframes). The skeletons consist of one dimensional line-segments, touching end-to-end, and occasionally branching. There are various way to do this.</p>
<p>In blender there is the 'skin' modifier, which works quite well, granted a few conditions. One such condition is that segments radiating from a branch point be sufficiently spaced out, otherwise branches interest each other (A). Another is that segments that branch away from connection points are not too short, relative to their neighbors (B). Finally, consecutive segments need to make a sufficiently obtuse angle between one another, otherwise a kink occurs in the mesh, causing self-intersection (C).
</p>

![skin_mod]({{ site.baseurl }}/images/problems_with_skin.png)
*Problems with Skin Modifier. From left to right: A, B and C*

<p>The issue with these resulting meshes is that they are often not 3d printable. Meshes that are 3d printable need to be water-tight, meaning that no faces are missing. Some 3d printing processing software also needs all the edges to be manifold. This means that each edge has exactly two faces connected to it. So in the general case of arbitrarily complex wire-frame skeletons, blenders skin modifier breaks down for 3d printing. The problem of skinning an arbitrary wire-frame skeleton so that it is 3d printable, with any number of small branch angles, tight turns, and tiny edges, is difficult. Some approaches, similar in effect to blender's skin modifier, attempt to create a structured, orderly polygonal mesh composed of regular rods connected by joints. One such method is<a href="http://www.viz.tamu.edu/faculty/ergun/research/topology/papers/bridges05.pdf"> described in this paper</a>, and has been used in this <a href="http://www.grasshopper3d.com/profiles/blogs/introducing-exoskeleton-a-wireframe-thickening-tool">grasshopper plugin</a>.</p>
<p>I found a work-around to this problem, that is guaranteed to always create water-tight, clean meshes. I made a script in blender that simply adds a <a href="https://docs.blender.org/manual/en/dev/modeling/metas/index.html">metaball</a> rod in place of each line-segment in the wire-frame (see <a href="https://en.wikipedia.org/wiki/Metaballs">https://en.wikipedia.org/wiki/Metaballs</a>, for a description of metaballs). Where metaball rods overlap they have an additive effect, so this results in slight lumps at the connection points. For the time being this is fine, but it is easy to imagine a specially shaped unitary metaball rod that has a tappered ends, so that when overlap occurs the node region has the same diameter as the rest of the rod. Also conceivable is a more complex program which could alter the size of the ends, so that nodes with many incoming segments are not unnecessarily large. Regardless, this is a neat technique for easily generating 3d-printable structures from blender wire-frames!</p>

![meta_rods]({{ site.baseurl }}/images/meta_rods.png)
*same wire frames, with metaball rods*

![meshed]({{ site.baseurl }}/images/meta_rods_meshed.png)
*metaballs converted to mesh, at low resolution so it is easy to see the facets. This is the final step before 3d printing.*

![meta_ear]({{ site.baseurl }}/images/meta_ear.png)
*with metball skinning funky geometry is totally fine*

![skin_smoothed_ear]({{ site.baseurl }}/images/skin_smoothed_ear.png)
*With the skin modifier there are weird gaps and creases. Some of these will mess up 3d printing.*

