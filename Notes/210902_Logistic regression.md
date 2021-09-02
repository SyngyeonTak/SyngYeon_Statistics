# Statistics_day210902=7

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

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/37533d8f-43a4-4f78-bb8c-54cc61bbcd20/Untitled.png)

### Logistic Regression

Logistic Regression is similar to linear regression, except...

Logistic regression predicts whether something is True or False, instead of predicting something continuous like size

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/997ffa7b-3cd9-4ed9-8844-0fa243cdb1ec/Untitled.png)

Also, instead of fitting a line to the data, logistic regression fits an "S" shaped "logistic function"

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5e425d03-a2ef-44d9-99d1-25f5390fda11/Untitled.png)

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

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3c3bb834-f2e3-4776-b727-94b5e2fc84b0/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ae892487-7192-4f17-ac2f-949a680235dd/Untitled.png)

and lastly you multiply all of those likelihoods together. That's the likelihood of the data given this line

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/24d27207-7405-448f-ae01-6e4d77c9cdae/Untitled.png)

Then you shift the line and calculate a new likelihood of the data

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9178e211-6ca6-42e1-812b-dcebaff5d933/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cf781d4a-78c7-46ef-84e1-e94adc5b9f9a/Untitled.png)