# day211101 - correlation coefficient

**Intro**

When I kaggle, I found covariance, correlation and coefficient are used for telling if the feature is significant.

But I hardly understand why they are so important. That is why I want to know how different they are and how interpret the numbers...

### C**ovariance**

![Untitled](day211101%20-%20correlation%20coefficient%20a2e040a3d31f401287d9f436eefead1f/Untitled.png)

It can't be too much to go over the covariance.

Covariance shows trends for the variables whether it is positive or negative

But we can't know how strong the trend is. And Covariance is so sensitive to the scale of the data

## **Correlation**

We can tell the things from correlation. Covariance is a stepping stone for correlation.

![Untitled](day211101%20-%20correlation%20coefficient%20a2e040a3d31f401287d9f436eefead1f/Untitled%201.png)

The correlation solves the scale problem to some degree.

When we calculate correlation, the denominator squeezes the covariance to be a number from -1 to 1.

In other words, the denominator ensures that the scale of the data does not effect the correlation value, and this makes correlations much easier to interpret