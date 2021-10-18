# day211018 - Gradient Boost (statquest 1)

Gradient Boost starts by making a single leaf not a tree or stump

This leaf represents an initial guess for the Weights of all of the samples

And it keeps going on to build a tree

Like AdaBoost, this tree is based on the errors made by the previous tree

### **The procedures for Gradient Boost**

The first thing we do is calculate the average Weight

The next thing we do is build a tree based on the errors from the first tree

The errors that the previous tree made are the differences between the Observed Weights and the predicted weight. And we get the difference, a Pseudo Residual