# Statistics_day210830=7

### Coefficient of Variation

You will notice the word "coefficient" used a lot in statistics

Coefficient of variation is CV for short

CV shows how much the data varies compared to the mean

Always expressed in a %

It's hard to explain with only one group of patients.

CV has no units - so you could compare two different ways of measuring a lab value, for example.

The CV is the measure of the spread of the data relative to the average of the data

The less CV is, the more stable, predictable the data is

### Chebyshev's Theorem

**What Chebyshev Figured out**

First, he started thinking like this:

If you have an x-bar and an s, you can create lower and upper limits by subtracting the s and adding the s to the x-bar.

You can do this in population version too

**For example, if I had N of 100 and an sd of 5:**

If i subtracted 1 sd from 100, I'd get 95 as the lower limit

If I add 1 sd to 100, I get 105 as the upper limit

I could event try this by doing 2 sds - meaning subtractin 10 for the lower limit and adding 10 for the upper limit

He realized if he used some urles along with his, there would be an interpretation of these limits that would be useful.

He figured out the upper and lower limits, when figured out this way, explained at leat what % of the data would be between these limis tin this dataset

he wanted this to work for all distributions, not just normal

He used a formula to figure out this % that was based on the s. He used "k" to mean the number of sd in the equation

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e05fd9b1-c975-4eaa-aecd-0555341c5f9b/Untitled.png)

### The message on Chebyshev Interval

It works for any distribution (normal, skewed, etc)

Chebyshev intervals tell you that at least a certain % is in the interval

Chebyshev intervals are sometimes non-sensical (negative numbers, very high limits)

## Percentiles and Box and Whisker plots

### Percentile

**What are Percentiles?**

Quantitative data

Remember Standardized tests...

Example: If you test at the 77th percentile, it means you did better than 77% of the people taking the test

If 100 people took the test, you'd have done better than 77 of them.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9b69074-fd95-45cc-b087-9fea747fb4fc/Untitled.png)

### Quartiles and Interquartile Range

**Quartiles is a specific set of percentiles**

1st quartile: 25th percentile

2nd quartile: 50th percentile

3rd quartile: 75th percentile

### Computing Quartiles

1. Order the data from smallest to largest
2. Find the median
3. Find the median of the lower half of the data
4. Find the median of the upper half of the data

**Interquartile range**

3rd quartile minus 1st quartile (IQR)

### Box-and-Whisker Plot

**Box Plot Ingredients**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/001e7b45-126d-4abd-a3e2-16e79daa7f0e/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4d07f736-16ce-4431-b25b-f24cd1f09e48/Untitled.png)