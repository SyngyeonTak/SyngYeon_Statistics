# day211023 - Gradient Boost Part (3) - Classification

**Before...**

Before I get into the new chapter, let's recap what gradient Boost is.

idea - To avoid overfitting, we have to figure out a way to predict the target variable.

If the observed values are continuous, we can start by setting the average as an initial predicted value. And we use the equation for the gradient boost. With this equation, we run down the trees and keep the predicted value close to the best value...

This is how I understand Gradient Boost

**Intro**

We are going to get into Gradient Boost with Classification  

log of the odds

The way to get an initial prediction is based on log(odds). With this value, we can get the probability and use it as the average of prediction.

![Untitled](day211023%20-%20Gradient%20Boost%20Part%20(3)%20-%20Classificati%20b926482af1384c8aa230e3ef3b6d3416/Untitled.png)

So... the 0.7 is the threshold for classification. And how could I get the Residual for better prediction?

The value for classes can be converted to 0(No) and 1(Yes).

So the observed values can have either 0 or 1. and get the residual from the difference between the observed value and prediction(= threshold).

![Untitled](day211023%20-%20Gradient%20Boost%20Part%20(3)%20-%20Classificati%20b926482af1384c8aa230e3ef3b6d3416/Untitled%201.png)

To get pseudo residual, we have to scale the output value derived from the previous residual. because the pseudo residual will be 0, if we just plug the value of residual in each leaf.

We used an average of the values for the regression, but we have to get a quite nasty(?) equation for classification, which looks like below...

![Untitled](day211023%20-%20Gradient%20Boost%20Part%20(3)%20-%20Classificati%20b926482af1384c8aa230e3ef3b6d3416/Untitled%202.png)

Then we scale the value by the learning rate

![Untitled](day211023%20-%20Gradient%20Boost%20Part%20(3)%20-%20Classificati%20b926482af1384c8aa230e3ef3b6d3416/Untitled%203.png)

![Untitled](day211023%20-%20Gradient%20Boost%20Part%20(3)%20-%20Classificati%20b926482af1384c8aa230e3ef3b6d3416/Untitled%204.png)

Since the value of each leaf is different from the first tree, we get different probability for each record from the second tree.

![Untitled](day211023%20-%20Gradient%20Boost%20Part%20(3)%20-%20Classificati%20b926482af1384c8aa230e3ef3b6d3416/Untitled%205.png)

We do the same thing until we have made the maximum number of trees specified, or the residuals get super small.

**Recap**

First, we get the probability based on log(odds).

Second, we get each residual from the difference between observed values and threshold.

Third, we get an output value resulted from the equation.

Fourth, we get a new log(odds) prediction scaled by the learning rate

→ previous residual * learning rate * (output) = new log(odds) prediction

Fifth, we get the probability from the log(odds) prediction

→ we do this multiple times and get the final probability

lastly, we compare the probability to the threshold and we tell what category the record is in