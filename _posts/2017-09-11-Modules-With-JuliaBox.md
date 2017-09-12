---
layout: post
category: programming
---

I am using [juliabox](https://www.juliabox.com/) to write code for the [Nonlinear Dynamics course](https://www.complexityexplorer.org/courses/79-nonlinear-dynamics-mathematical-and-computational-approaches-fall-2017) over at the complexity explorer. The complexity explorer is a project setup by the [Santa-Fe institute](https://www.santafe.edu/). Check it out. It's awesome.

I like to call nonlinear dynamics "blobby-math." I am so stoked about the class!

Anyway I want to use the new-ish scientific computing language [Julia](https://julialang.org/). And I wrote a few functions that make sense as a module, and I want to now import that module in another file in juliabox. How to do??

Here is what I found:
1. Import the [NBInclude Package](https://github.com/stevengj/NBInclude.jl)
2. Use the nbinclude to include your jupyter (.ipynb) file

{% highlight julia %}
Pkg.add("NBInclude")
using NBInclude
nbinclude("name_of_your_file.ipynb")
using name_of_your_file
{% endhighlight %}

It worked! Took me a bit to realize that it actually was that easy!
The nbinclude() will run all the cells in your jupter file.
[Julia's module documentation](https://docs.julialang.org/en/stable/manual/modules/).

