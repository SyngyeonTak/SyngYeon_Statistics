# day210909 - Naive Bayes Algorithms

[https://www.geeksforgeeks.org/naive-bayes-classifiers/](https://www.geeksforgeeks.org/naive-bayes-classifiers/)

This article discusses the theory behind the Naive Bayes classifiers and their implementation.

Naive Bayes classifiers are a collection of classification algorithms based on **Bayes’ Theorem**. It is not a single algorithm but a family of algorithms where all of them share a common principle, i.e. every pair of features being classified is independent of each other.

To start with, let us consider a dataset.

Consider a fictional dataset that describes the weather conditions for playing a game of golf. Given the weather conditions, each tuple classifies the conditions as fit(“Yes”) or unfit(“No”) for plaing golf.

Here is a tabular representation of our dataset.

![Untitled](day210909%20-%20Naive%20Bayes%20Algorithms%20fd3ee831b0d749ac8f90fca46f243fe3/Untitled.png)

The dataset is divided into two parts, namely, **feature matrix** and the **response vector**.

- Feature matrix contains all the vectors(rows) of dataset in which each vector consists of the value of **dependent features**. In above dataset, features are ‘Outlook’, ‘Temperature’, ‘Humidity’ and ‘Windy’.
- Response vector contains the value of **class variable**(prediction or output) for each row of feature matrix. In above dataset, the class variable name is ‘Play golf’.

**Assumption:**

**Bayes’ Theorem**

Bayes’ Theorem finds the probability of an event occurring given the probability of another event that has already occurred. Bayes’ theorem is stated mathematically as the following equation:

$$P(A|B) = \frac{P(B|A)P(A)}{P(A)}$$

where A and B are events and P(B) ? 0.

- Basically, we are trying to find probability of event A, given the event B is true. Event B is also termed as **evidence**.
- P(A) is the **priori** of A (the prior probability, i.e. Probability of event before evidence is seen). The evidence is an attribute value of an unknown instance(here, it is event B).
- P(A|B) is a posteriori probability of B, i.e. probability of event after evidence is seen.

Now, with regards to our dataset, we can apply Bayes’ theorem in following way:

![https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-e85875a7ff9e9b557eab6281cc7ff078_l3.svg](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-e85875a7ff9e9b557eab6281cc7ff078_l3.svg)

where, y is class variable and X is a dependent feature vector (of size *n*) where:

![https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-5385a4693c3fb17811cf36593978a601_l3.svg](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-5385a4693c3fb17811cf36593978a601_l3.svg)

Just to clear, an example of a feature vector and corresponding class variable can be: (refer 1st row of dataset)

```
X = (Rainy, Hot, High, False)
y = No

```

So basically, P(y|X) here means, the probability of “Not playing golf” given that the weather conditions are “Rainy outlook”, “Temperature is hot”, “high humidity” and “no wind”.

### Naive assumption

Now, its time to put a naive assumption to the Bayes’ theorem, which is, **independence** among the features. So now, we split **evidence** into the independent parts.

Now, if any two events A and B are independent, then,

```
P(A,B) = P(A)P(B)

```

Hence, we reach to the result:

![https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-1c3f5ab570cf0ab3f43d5c18c645b67a_l3.svg](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-1c3f5ab570cf0ab3f43d5c18c645b67a_l3.svg)

which can be expressed as:

![https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-8171c1fe2cbd3ed62bc3f40d682c0512_l3.svg](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-8171c1fe2cbd3ed62bc3f40d682c0512_l3.svg)

Now, as the denominator remains constant for a given input, we can remove that term:

![https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-c778553cb5a67518205ac6ea18502398_l3.svg](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-c778553cb5a67518205ac6ea18502398_l3.svg)

Now, we need to create a classifier model. For this, we find the probability of given set of inputs for all possible values of the class variable *y* and pick up the output with maximum probability. This can be expressed mathematically as:

![https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-f3637f468262bfbb4accb97da8110028_l3.svg](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-f3637f468262bfbb4accb97da8110028_l3.svg)