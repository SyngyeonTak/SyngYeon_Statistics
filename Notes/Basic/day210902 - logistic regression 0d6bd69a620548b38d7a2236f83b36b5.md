# day210902 - logistic regression

### Before begin...

**p-value**

In statistics, the p-value is the probability of obtaining results at least as extreme as the observed results of a statistical hypothesis test, assuming that the null hypothesis is correct. ... A smaller p-value means that there is stronger evidence in favor of the alternative hypothesis.

### Linear Regression

Two variables (independent, dependent)

1) Calculate R square

2) Get p_value

### Multiple Regression

There are Three Variables (2 independents, 1 dependent)

1) Calculate R square

2) Get p_value

![Untitled](day210902%20-%20logistic%20regression%200d6bd69a620548b38d7a2236f83b36b5/Untitled.png)

### Logistic Regression

Logistic Regression is similar to linear regression, except...

Logistic regression predicts whether something is True or False, instead of predicting something continuous like size

![Untitled](day210902%20-%20logistic%20regression%200d6bd69a620548b38d7a2236f83b36b5/Untitled%201.png)

Also, instead of fitting a line to the data, logistic regression fits an "S" shaped "logistic function"

![Untitled](day210902%20-%20logistic%20regression%200d6bd69a620548b38d7a2236f83b36b5/Untitled%202.png)

This means that the curve tells us the probability that a mouse is obese based on its weight

Although logistic regression tells the probability that a mouse is obese or not, it's usually used for classification

For example, if the probability a mouse is obese is more than 50%, then we'll classify it as obese, otherwise, we'll classify it as "not obese"

Logistic regression's ability to provide probabilities and classify new samples using continuous and discrete measurements makes it a popular machine learning method

### The difference between Linear Regression and Logistic Regression

Linear Regression: using residuals to calculate R squared.

Logistic Regression: it doesn't have the same concept of a "residual". So it can't use least squares and it can't calculate R squared

Instead, it uses something called "maximum likelihood".

Maximum likelihood

In statistics, maximum likelihood estimation is a method of estimating the parameters of an assumed probability distribution, given some observed data. This is achieved by maximizing a likelihood function so that, under the assumed statistical model, the observed data is most probable.

a statistical method for estimating population parameters (such as the mean and variance) from sample data that selects as estimates those parameter values maximizing the probability of obtaining the observed data.

use Maximum likelihood to calculate the likelihood of observing a non-obese mouse that weighs this much

![Untitled](day210902%20-%20logistic%20regression%200d6bd69a620548b38d7a2236f83b36b5/Untitled%203.png)

![Untitled](day210902%20-%20logistic%20regression%200d6bd69a620548b38d7a2236f83b36b5/Untitled%204.png)

and lastly you multiply all of those likelihoods together. That's the likelihood of the data given this line

![Untitled](day210902%20-%20logistic%20regression%200d6bd69a620548b38d7a2236f83b36b5/Untitled%205.png)

Then you shift the line and calculate a new likelihood of the data

![Untitled](day210902%20-%20logistic%20regression%200d6bd69a620548b38d7a2236f83b36b5/Untitled%206.png)

![Untitled](day210902%20-%20logistic%20regression%200d6bd69a620548b38d7a2236f83b36b5/Untitled%207.png)