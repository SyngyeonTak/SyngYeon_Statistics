# day210907 - Bias and Variance - 1

Imagine we measured the weight and height of a bunch of mice and plotted the data on a graph

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled.png)

Ideally, we would know the exact mathematical formula that describes the relationship between weight and height

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%201.png)

...but, in this case, we don't know the formula, so we're going to use two machine learning methods to approximate this relationship

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%202.png)

The first thing we do is split the data into two sets, one for training the machine learning algorithms and one for testing them.

Blue dots are the training set

Green dots are the testing set

- What is the difference between the training set and the testing set

    The “training” data set is the general term for the samples used to create the model, while the “test” or “validation” data set is used to qualify performance. Perhaps traditionally the dataset used to evaluate the final model performance is called the “test set”.

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%203.png)

The first machine learning algorithm that we will use is Linear Regression (aka "Least Squares").

Note: The Straight Line doesn't have the flexi

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%204.png)

No matter how we try to fit the line, it will never curve

Thus, the Straight Line will never capture the true relationship between weight and height, no matter how well we fit it to the training set.

The inability for a machine learning method (like linear regression) to capture the true relationship is called bias

Another machine learning method might fit a Squiggly Line to the Training set

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%205.png)

The Squiggly Line is super flexible and hugs the training set along the arc of the true relationship

Because the Squiggly Line can handle the arc in the true relationship between weight and height, it has very little bias

We can compare how well the Straight Line and the Squiggly Line fit the training set by calculating their sums of squares.

In other words, we measure the distances from the fit lines to the data, square them and add them up.

Notice how the Squiggly Line fits the data so well that the distances between the line and the data are all 0

In the contest to see whether the Straight Line fits the training set better than the Squiggly Line.

The Squiggly line winds

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%206.png)

But remember, so far we've only calculated the Sums of Squares for the training set

We also have a testing set

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%207.png)

Now let's calculate the Sums of Squares for the testing set

In the contest to see whether the Straight Line fits the testing set better than the Squiggly Line...

The Straight Line wins

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%208.png)

Even though Squiggly Line did a great job fitting the training set

It did a terrible job fitting the testing set

In Machine Learning lingo, the difference in fits between data sets is called Variance

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%209.png)

The Squiggly Line has low bias, since it is flexible and can adapt to the curve in the relationship between weight and height.

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%2010.png)

But the Squiggly Line has high variability, because it results in vastly different Sums of Squares for different datasets.

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%2011.png)

In other words, it's hard to predict how well the Squiggly Line will perform with future data sets. It might do well sometimes, and other times it might do terribly.

In contrast, the Straight Line has relatively high bias, since it can not capture the curve in the relationship between weight and height.

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%2012.png)

But the straight Line has relatively low variance, because the Sums of Squares are very similar for different datasets

![Untitled](day210907%20-%20Bias%20and%20Variance%20-%201%2072e540d30df84ba88d3df710074ad52c/Untitled%2013.png)