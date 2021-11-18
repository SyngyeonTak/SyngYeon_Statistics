# day211108 - How to compare box plots

[https://blog.bioturing.com/2018/05/22/how-to-compare-box-plots/](https://blog.bioturing.com/2018/05/22/how-to-compare-box-plots/)

The key information you want to get when reading box plots is: are these groups different, and if so, how? To quickly compare box plots, look for these things:

# **The boxes:**

Start with the boxes. They represent the interquartile range, or the middle half of the values in each group. If two boxes do *not* overlap with one another, say, box A is completely above or below box B, then there *is* a difference between the two groups.

![https://blog.bioturing.com/wp-content/uploads/2018/11/parallel-non-overlapped-box-plots.png](https://blog.bioturing.com/wp-content/uploads/2018/11/parallel-non-overlapped-box-plots.png)

*Non-overlapping boxes, groups are different.*

If they overlap, move on to the lines inside the boxes.

# **The middle lines:**

These are the medians, the “middle” values of each group. If the median line of box A lies outside of box B entirely, then there is *likely* to be a difference between the two groups.

![https://blog.bioturing.com/wp-content/uploads/2018/05/overlapping-box.jpg](https://blog.bioturing.com/wp-content/uploads/2018/05/overlapping-box.jpg)

*Boxes overlap but don’t spread past both medians: groups are likely to be different.*

If both median lines lie within the overlap between two boxes, we will have to take another step to reach a conclusion about their groups.

# **The whiskers:**

The lines coming out from each box extend from the maximum to the minimum values of each set. Together with the box, the whiskers show how big a range there is between those two extremes. Larger ranges indicate wider distribution, that is, more scattered data.

The same thing can be said about the boxes. Short boxes mean their data points consistently hover around the center values. Taller boxes imply more variable data. That’s something to look for when comparing box plots, especially when the medians are similar.

![https://blog.bioturing.com/wp-content/uploads/2018/05/biovinci-box-plot.png](https://blog.bioturing.com/wp-content/uploads/2018/05/biovinci-box-plot.png)

*Wider ranges (whisker length, box size) indicate more variable data.*

# **Outliers:**

When there are outliers, they are dotted outside the whiskers. Not all datasets have outliers. Data points have to go above or below the box pretty far to count as outliers. How far? 1.5 times the size of the box.

![https://blog.bioturing.com/wp-content/uploads/2018/05/BioVinci-box-and-whisker-plot.png](https://blog.bioturing.com/wp-content/uploads/2018/05/BioVinci-box-and-whisker-plot.png)

# **To sum up:**

That’s a quick and easy way to compare two box-and-whisker plots. First, look at the boxes and median lines to see if they overlap. Then check the sizes of the boxes and whiskers to have a sense of ranges and variability. Finally, look for outliers if there are any.

[BioVinci](https://vinci.bioturing.com/) is a drag-and-drop software that will let you make a box plot in just a few minutes.

If you want to know what else is in the box (hah, see what I did there?), [check out this post](https://blog.bioturing.com/2018/05/22/more-on-how-to-compare-box-plots/). We’ll cover:

- How to compare box plots with overlapping medians.
- Ranges vs counts: a common mistake while reading box plots.
- Box plots skewed to the right? To the left?
- Limitations of box plots, and better alternatives.