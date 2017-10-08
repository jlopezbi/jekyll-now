---
layout: work
published: true
status: publish
categories: []
tags: []
meta:
  work-client: ''
  work-desc-position: bottom
  work-url: http://golancourses.net/2013/projects/study-for-biomimetic-heat-sinks-coral-growth/
author:
  login: jlopezbi
  email: joshlobinder@gmail.com
  display_name: jlopezbi
  first_name: Joshua
  last_name: Lopez-Binder
excerpt: A simulation of coral growth with the intent to generate complex heat-sink
  geometry. Coded in RhinoPython
---

{% include image.html name="morphological_plasticity.png" %}

{% include image.html name="smallLineage_flatPlate.png" %}

## Summary
This project simulates coral growth. A computational model was built using python and the CAD software Rhino. This program created 3D branching structures similar to stony corals.

## The Engineering Idea: Heat-Transfer Mechanisms
The initial aim was to eventually add to the model heat transfer, and grow shapes that serve as effective heat-transfer mechanisms. A special class of heat-transfer devices called Heat Sinks are commonly used to cool electronic components. Heat sinks must meet seemingly conflicting requirements: high surface area, large cross-sectional area, and geometry that allows fluid to flow over the surface. It seemed to me like coral-colonies face a similar set of challenges. *After working on this project I learned about nanoscale bio-sensors. This class of devices appears to be a much closer analog for sort of challenges coral-colonies face.*

The project became primarily focused on simply modeling coral growth. A detailed video explanation including the heat-sink idea is [here](https://vimeo.com/66499717)


## The Science Idea: Modeling Adaptive Plasticity in Coral Colonies.
The project really became about modeling coral growth.

Corals are colonial organisms, composed of thousands of tiny polyps, which resemble small sea anemones. Polyps eat organic matter that drifts near them in the water. They also photosynthesize, thanks to a symbiosis with an algae that lives in their tissue called zooxanthellae. 

A single coral species can exhibit a wide range of forms according to conditions like light, flow and competition from other colonies. This is 'plasticity' in the shape the colony takes. Further, it seems that the shapes that the colonies form are adapted to the specific environmental condition. So coral's seem to exhibit "adaptive plasticity." For example, colonies in low-light tend to fan-out, while colonies in fast-moving water tend to stay more stubby and have columns. These growth patterns arise not from coordination mediated by a centralized controller, but instead from the result of behaviors that each polyp exhibits.[1]

Framed in the context of science this project explores the question "Can adaptive plasticity arise from a simple computational model of a coral-colony?"

For more info about how the simulation works go [here](https://github.com/jlopezbi/DLA_heatSink). Much of the inspiration for this project came from this book: [The Algorithmic Beauty of Seaweeds, Sponges and Corals](http://www.springer.com/computer/theoretical+computer+science/book/979-3-540-67700-0), as well as [this work](http://homepages.cwi.nl/~merks/Publications/Corals.html)

{% include image.html name="square_3dprint.jpg" caption="A 3d print of a simulated coral colony." %}

{% include image.html name="aluminum_cast.jpg" caption="An aluminum cast of a 3d print." %}

