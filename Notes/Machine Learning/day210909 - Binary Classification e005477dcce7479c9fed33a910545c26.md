# day210909 - Binary Classification

# A Closer Look At Binary Classification.

As we’ve already discussed and as its name implies, binary classification in deep learning refers to the type of classification where we have two class labels – one normal and one abnormal. Some examples of binary classification use:

- To detect whether email is spam or not
- To determine whether or not a patient has a certain disease in medicine.
- To determine whether or not quality specifications were met when it comes to QA (Quality Assurance).

For example, the normal class label would be that a patient has the disease, and the abnormal class label would be that they do not, or vice-versa.

As is with every other type of classification, it is only as good as the binary classification dataset that it has – or, in other words, the more training and data it has, the better it is.

### Binary Classification Algorithms

There are quite a few different algorithms used in binary classification. The two that are designed with only binary classification in mind (meaning they do not support more than two class labels) are Logistic Regression and Support Vector Machines. A few other algorithms are: Nearest Neighbours, Decision Trees, and Naive Bayes.

- **Logistic Regression** – It’s a machine learning classification algorithm that employs one or more independent variables to produce a result. A dichotomous variable is used to assess the result, which means there are only two potential results. The purpose of logistic regression is to identify the best fit between a dependent variable and a collection of independent variables. It outperforms other binary classification algorithms such as closest neighbor because it quantifies the elements that lead to categorization.
- **Support Vector Machine** – The support vector machine is a classification algorithm that depicts training data as points in space split into categories by as large a distance as feasible. After then, new points are added to space by guessing which category they will fall into and which space they will occupy. Its decision function employs a subset of training points, making it memory economical and very effective in high-dimensional spaces. The support vector machine’s sole drawback is that the approach does not immediately offer probability estimations.