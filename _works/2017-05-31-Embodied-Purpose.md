---
layout: work
---


{% include image.html name="side_view_all.jpg" %}

{% include image.html name="main_image_all_3d.jpg" %}

{% include image.html name="detail.jpg" %}

{% include image.html name="most_branches.jpg" %}

{% include image.html name="compromise_colonies.jpg" %}

{% include image.html name="highest_avg_satisfaction_colonies.jpg" %}


# This sculpture is about collections of creatures that live together in colonies.
I imagined a toy-world where there are two basic factors that affect the ‘fitness’ of a colony. The first factor is population size (p), determined by the number of branches. The second factor is the distribution of resources, or ‘satisfaction’ (s) of each branch in the colony. For an unbalanced colony a large population may go hand-in-hand with a failure to provide resources to the majority. Or vice versa. This imbalance is happening in the colonies on either end of the row. Here are the fitness-scores of all of the colonies in this sculpture, from left to right:

( population, satisfaction-score )

(185, 5 ), ( 116, 7 ),  ( 104, 9 ),  ( 76, 15 ),  ( 46, 22 ),  ( 23, 43 ),  ( 16, 62 )


# How did these shapes come about?
<p>These colonies were evolved in a computer program and then fabricated using a 3d printer.</p>

This <a href="https://github.com/jlopezbi/ColonyEvolver">code project</a> implemented a simulated world loosely based on coral-growth (coral is a colonial organism). Each colony has a different growth-rule that interacts with the simulated world. These growth rules were evolved to produce shapes that had high fitness (p and s). The seven shapes in this sculpture are a representative sample from a final population of 80 individuals. These final seven evolved together and have some shared ‘genetic material’ between them. Genetic material in this case is the growth-rule itself.

<p>Every colony starts as a single vertical branch, the ‘seed’. Nutrients in the form of spheres rain down on the seed. Any branch can grow a new branch when a sphere drops on it. Where and when a new branch gets added is decided by the growth-rule, expressed as a simplified computer program.</p>

<p>A randomly generated population of growth-rules started the evolution, and in each generation only the fittest survived to replicate and ‘mate’. The small changes from mating and mutation slowly lead to a population that has higher fitness than the original.</p>

Dimensions: 47 x 8 x 9 in
