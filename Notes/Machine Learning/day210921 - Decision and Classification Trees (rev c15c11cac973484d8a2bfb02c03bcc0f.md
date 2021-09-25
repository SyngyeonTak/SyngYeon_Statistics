# day210921 - Decision and Classification Trees (revision)

When a Decision Tree classifies things into categories, it's called a Classification Tree

When a Decision Tree predicts numeric values, it's called a Regression Tree

![Untitled](day210921%20-%20Decision%20and%20Classification%20Trees%20(rev%20c15c11cac973484d8a2bfb02c03bcc0f/Untitled.png)

Because these three Leaves all contain a mixture of people who do and do not Love Cool As Ice

They are called Impure

In contrast, the Leaf that only contains people who do not Love Cool As Ice 

We could assume Soda can predict whether observations like Cool As Ice or not

But we better quantify the predictions

The good news is that there are several ways to quantify the Impurity of the leaves

Gini impurity, Entropy, and Information Gain...

Overfit - meaning our tree does well with the original data, but it doesn't do well with any other data set.