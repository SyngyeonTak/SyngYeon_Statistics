# day210905 Sampling Distributions and the Central Limit Theorem

### Parameters, Statistics, and Inferences

### a Reminder of statistic and Parameter

A statistic is a numerical measure describing a sample

A parameter is a numerical measure describing a population

![Untitled](day210905%20Sampling%20Distributions%20and%20the%20Central%20L%209a84835cc75c415497c85689f67c867c/Untitled.png)

### Inferences

Estimation: We estimate the value of a population parameter using a sample

Testing: We do a test to help us make a decision about a population parameter

Regression: We make predictions or forecasts about a statistic

### Frequency vs. Sampling Distribution

**Frequency Distribution**

1. make a histogram of a quantitative variable
2. Draw the shape and name the distribution

**Sampling Distribution**

1. Start with a population
2. Decide on an n.
3. Take as many samples of n as possible from the population
4. Make an x-bar for each sample
5. Make a histogram of all the x-bars.

A sampling distribution is a probability distribution of a sample statistic based on all possible simple random samples of the same size from the same population

In the next section, we will talk about the Central Limit Theorem, which is a proof that shows how we can use a sampling distribution for inference

### Central Limit Theorem

For any normal distribution:

1. The sampling distribution (the distributions of x-bars from all possible samples) is also a normal distribution
2. The mean of the x-bars is actually mu
3. The standard deviation of the x-bars is actually sd / mu

![Untitled](day210905%20Sampling%20Distributions%20and%20the%20Central%20L%209a84835cc75c415497c85689f67c867c/Untitled%201.png)

1. If the distribution of x is normal, then the distribution of x-bar is also normal

![Untitled](day210905%20Sampling%20Distributions%20and%20the%20Central%20L%209a84835cc75c415497c85689f67c867c/Untitled%202.png)

1. Even if the distribution of x is NOT normal, as long as n≥30, the Central Limit Theorem says that the x-bar distribution is approximately normal

![Untitled](day210905%20Sampling%20Distributions%20and%20the%20Central%20L%209a84835cc75c415497c85689f67c867c/Untitled%203.png)

### Finding Probabilities Regarding X-bar

How to Find Probabilities Regarding X-Bar

1. Convert x-bar to a z-score using the following formula:

![Untitled](day210905%20Sampling%20Distributions%20and%20the%20Central%20L%209a84835cc75c415497c85689f67c867c/Untitled%204.png)

1. Look up the probability for the z-score in the z-table (like in Chapters 7.2 - 7.3, only this is about x-bar).

### What is Standard Error

The standard error (SE) of a statistic is the standard deviation of its sampling distribution or an estimate of that standard deviation

### Why do we use Standard Error

If we want to indicate the uncertainty around the estimate of the mean measurement, we quote the standard error of the mean. The standard error is most useful as a means of calculating a confidence interval. For a large sample, a 95% confidence interval is obtained as the values 1.96×SE either side of the mean.

### Standard Deviation vs Standard Error

The standard deviation quantifies the variation within a set of measurements.

![Untitled](day210905%20Sampling%20Distributions%20and%20the%20Central%20L%209a84835cc75c415497c85689f67c867c/Untitled%205.png)

The standard error quantifies the variation in the means from multiple sets of measurements 

 

![Untitled](day210905%20Sampling%20Distributions%20and%20the%20Central%20L%209a84835cc75c415497c85689f67c867c/Untitled%206.png)

The confusing thing is that the standard error can be estimated from a single set of measurements, even though it describes the means from multiple sets. Thus, even if you only have a single set of measurements, you are often given the option to plot the standard error.