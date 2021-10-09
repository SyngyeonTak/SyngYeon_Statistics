# day211006 - Standardization

[https://www.analyticsvidhya.com/blog/2020/04/feature-scaling-machine-learning-normalization-standardization/](https://www.analyticsvidhya.com/blog/2020/04/feature-scaling-machine-learning-normalization-standardization/)

### **Feature Scaling for Machine Learning: Understanding the Difference Between Normalization vs. Standardization**

## **Introduction to Feature Scaling**

I was recently working with a dataset from an [ML Course](https://blackbelt.analyticsvidhya.com/bundles/machine-learning-course-online-certification-training-program) that had multiple features spanning varying degrees of magnitude, range, and units. This is a significant obstacle as a few machine learning algorithms are highly sensitive to these features.

I’m sure most of you must have faced this issue in your projects or your learning journey. For example, one feature is entirely in kilograms while the other is in grams, another one is liters, and so on. How can we use these features when they vary so vastly in terms of what they’re presenting?

> This is where I turned to the concept of feature scaling. It’s a crucial part of the data preprocessing stage but I’ve seen a lot of beginners overlook it (to the detriment of their machine learning model).
> 

![https://cdn.analyticsvidhya.com/wp-content/uploads/2020/04/Feature-image-Normalization-vs.-Standardization.png](https://cdn.analyticsvidhya.com/wp-content/uploads/2020/04/Feature-image-Normalization-vs.-Standardization.png)

Here’s the curious thing about feature scaling – it improves (significantly) the performance of some machine learning algorithms and does not work at all for others. What could be the reason behind this quirk?

Also, what’s the difference between normalization and standardization? These are two of the most commonly used feature scaling techniques in machine learning but a level of ambiguity exists in their understanding. When should you use which technique?

I will answer these questions and more in this article on feature scaling. We will also implement feature scaling in Python to give you a practice understanding of how it works for different machine learning algorithms.

*Note: I assume that you are familiar with Python and core machine learning algorithms. If you’re new to this, I recommend going through the below courses:*

## **Why Should we Use Feature Scaling?**

The first question we need to address – why do we need to scale the variables in our dataset? Some machine learning algorithms are sensitive to feature scaling while others are virtually invariant to it. Let me explain that in more detail.

## **What is Normalization?**

**Normalization is a scaling technique in which values are shifted and rescaled so that they end up ranging between 0 and 1. It is also known as Min-Max scaling.**

Here’s the formula for normalization:

![Untitled](day211006%20-%20Standardization%2079cf6749f9bc4fb78af768e548bf6061/Untitled.png)

Here, Xmax and Xmin are the maximum and the minimum values of the feature respectively.

- When the value of X is the minimum value in the column, the numerator will be 0, and hence X’ is 0
- On the other hand, when the value of X is the maximum value in the column, the numerator is equal to the denominator and thus the value of X’ is 1
- If the value of X is between the minimum and the maximum value, then the value of X’ is between 0 and 1

## **What is Standardization?**

**Standardization is another scaling technique where the values are centered around the mean with a unit standard deviation. This means that the mean of the attribute becomes zero and the resultant distribution has a unit standard deviation.**

Here’s the formula for standardization:

![Untitled](day211006%20-%20Standardization%2079cf6749f9bc4fb78af768e548bf6061/Untitled%201.png)

Note that in this case, the values are not restricted to a particular range.

Now, the big question in your mind must be when should we use normalization and when should we use standardization? Let’s find out!

## **The Big Question – Normalize or Standardize?**

Normalization vs. standardization is an eternal question among machine learning newcomers. Let me elaborate on the answer in this section.

- Normalization is good to use when you know that the distribution of your data does not follow a Gaussian distribution. This can be useful in algorithms that do not assume any distribution of the data like K-Nearest Neighbors and Neural Networks.
- Standardization, on the other hand, can be helpful in cases where the data follows a Gaussian distribution. However, this does not have to be necessarily true. Also, unlike normalization, standardization does not have a bounding range. So, even if you have outliers in your data, they will not be affected by standardization.

However, at the end of the day, the choice of using normalization or standardization will depend on your problem and the machine learning algorithm you are using. There is no hard and fast rule to tell you when to normalize or standardize your data. **You can always start by fitting your model to raw, normalized and standardized data and compare the performance for best results.**

It is a good practice to fit the scaler on the training data and then use it to transform the testing data. This would avoid any data leakage during the model testing process. Also, the scaling of target values is generally not required.