---
layout: post
title:  "Making venn diagram in R"
date:   2021-01-01 18:57:57 -0400
categories: jekyll update
---


Setting Up VennDiagram Package

In the examples of this R tutorial, we’ll use functions provided by the VennDiagram add-on package for the R programming language. In order to use the functions of VennDiagram, we need to install and load the package first:

{% highlight bash %}
install.packages("VennDiagram")                       # Install VennDiagram package
library("VennDiagram")                                # Load VennDiagram package
{% endhighlight %}

Pairwise Venn Diagram

The VennDiagram package provides functions for the production of venn diagrams of basically every number of sets (i.e. circles). The draw.pairwise.venn is used to draw pairwise venn diagrams.

If we want to apply the draw.pairwise.venn command, we need to specify the sizes of the areas of both sets as well as the intersection of the two sets:
{% highlight bash %}
grid.newpage()                                        # Move to new plotting page
draw.pairwise.venn(area1 = 10,                        # Create pairwise venn diagram
                   area2 = 20,
                   cross.area = 2)
{% endhighlight %}

Venn Diagram with Three Sets

Similar to the R programming code of Example 2, we can use the draw.triple.venn function to create a venn diagram with three sets. Note that this time we need to specify three different area values as well as the pairwise intersections and the intersection area of all sets:
{% highlight bash %}
grid.newpage()                                        # Move to new plotting page
draw.triple.venn(area1 = 10,                          # Create venn diagram with three sets
                 area2 = 20,
                 area3 = 15,
                 n12 = 2,
                 n23 = 3,
                 n13 = 7,
                 n123 = 2)
{% endhighlight %}

Change Color of Venn Diagram

In Example 4, I’ll show you how to make a venn diagram with colored lines around the circles and a filling color of the circles. The following R code is the same as in Example 3, but in addition we are specifying the line color to be red and the filling color to be blue (with the HEX-code #1b98e0). Have a look at the output:
{% highlight bash %}
grid.newpage()                                        # Move to new plotting page
draw.triple.venn(area1 = 10,                          # Change color of venn diagram
                 area2 = 20,
                 area3 = 15,
                 n12 = 2,
                 n23 = 3,
                 n13 = 7,
                 n123 = 2,
                 col = "red",
                 fill = "#1b98e0")
{% endhighlight %}

Specify Different Color for Each Set

We can also specify a different color for each of the sets of our venn diagram. For this task, we need to set the fill argument to be equal to a vector of colors. Each element of this vector is defining the color of one of the circles:

{% highlight bash %}
grid.newpage()                                        # Move to new plotting page
draw.triple.venn(area1 = 10,                          # Different color for each set
                 area2 = 20,
                 area3 = 15,
                 n12 = 2,
                 n23 = 3,
                 n13 = 7,
                 n123 = 2,
                 col = "red",
                 fill = c("pink", "green", "orange"))
{% endhighlight %}


Disable Transparency of Venn Diagram
You may have noticed that the previous venn diagrams are transparent, i.e. showing the intersections in a mixed and overlapping color. If we want to reduce or even disable this transparency, we can use the alpha argument of the VennDiagram functions. An alpha of 1, as shown below, is disabling the transparency completely:
{% highlight bash %}
grid.newpage()                                        # Move to new plotting page
draw.triple.venn(area1 = 10,                          # Disable transparency of venn diagram
                 area2 = 20,
                 area3 = 15,
                 n12 = 2,
                 n23 = 3,
                 n13 = 7,
                 n123 = 2,
                 col = "red",
                 fill = c("pink", "green", "orange"),
                 alpha = 1)
{% endhighlight %}

Remove Lines from Venn Diagram

The VennDiagram functions provide the possibility to remove the lines around the circles by specifying the lty argument to be equal to blank. Let’s do this in practice:
{% highlight bash %}
grid.newpage()                                        # Move to new plotting page
draw.triple.venn(area1 = 10,                          # Remove lines from venn diagram
                 area2 = 20,
                 area3 = 15,
                 n12 = 2,
                 n23 = 3,
                 n13 = 7,
                 n123 = 2,
                 fill = c("pink", "green", "orange"),
                 lty = "blank")
{% endhighlight %}

Add Name to Each Set of Venn Diagram

Finally, I want to show you how to assign category names (or labels) to each of our sets. We can do that by assigning a vector of category names to the category option of the VennDiagram functions:
{% highlight bash %}
grid.newpage()                                        # Move to new plotting page
draw.triple.venn(area1 = 10,                          # Add name to each set
                 area2 = 20,
                 area3 = 15,
                 n12 = 2,
                 n23 = 3,
                 n13 = 7,
                 n123 = 2,
                 fill = c("pink", "green", "orange"),
                 lty = "blank",
                 category = c("Group 1", "Group 2", "Group 3"))
{% endhighlight %}


{% highlight bash %}
{% endhighlight %}

{% highlight bash %}
{% endhighlight %}


Check out the [venndiagram R package][venndiagram] for more info on how to get the most out of venndiagram.
[venndiagram]: https://www.rdocumentation.org/packages/VennDiagram/versions/1.6.20
