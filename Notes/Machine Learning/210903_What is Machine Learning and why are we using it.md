# Statistics_day210818=7

In our daily lives, let's take a example that all people can relate. The algorithm behind Facebook' News feed make it personalized. It exploits user's data and feedback.

What is machine learning exactly?

"Machine learning is the science of getting computers to realize a task without being explicitly programmed"

Machine learning algorithms are given general guidelines that define the model, along with data. This data should contain the missing information necessary for the model to complete the task. So, a machine learning algorithm can accomplish its task when the model has been adjusted with respect to the data. We say that we "fit the model on the data" or that "the model has to be trained on the data"

Let’s illustrate this with a simple example. Let’s say we want to predict the price of a house based on the size of the house, the size of its garden, and the number of rooms it has.

We could build a machine learning algorithm. First, such algorithm would define a model that can be an incomplete formula created from our limited knowledge. Then, the model would be adjusted by training on given housing prices examples. Doing so, we combine a model with some data.

### Supervised and unsupervised models

**Supervised learning**

We want to get a model to predict the label of data based on their features. In order to learn mapping between features and labels, the model has to be fitted on given examples of features with their related labels. We say that "the model is trained on a labeled dataset"

Predicted labels can be numbers or categories. For example, we could be building a model that predicts the price of a house, implying we would want to predict a label that’s a number. In this case, we would talk about a regression model. Otherwise, we might also want to define a model that predicts a category, like “cat” or “not cat”, based on given features. In this situation, we would talk about a classification model.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68b0bdc7-f725-4f60-9acc-caeea0cdb09a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0aa6765e-8419-49cd-b404-59845fd2d2a8/Untitled.png)

**Unsupervised learning**

In unsupervised learning, we want to define a model that reveals structures in some data that are described only by their features but with no labels.

For example, unsupervised learning algorithms can help answer questions like “are there groups among my data?” or “is there any way to simplify the description of my data?”.

The model can look for different kind of underlying structures in the data. If it tries to find groups among the data we would talk about a clustering model. An example of a clustering model would be a model that segments customers of a company based on their profiles. Otherwise, if we have a model that transforms data and represents them with a smaller number of features, we would talk about a dimension reduction model. An example of this would be a model that summarises the multiple technical characteristics of some cars into a few main indicators.

**feature in statistics**

In machine learning and pattern recognition, a feature is an individual measurable property or characteristic of a phenomenon. ... The concept of "feature" is related to that of explanatory variable used in statistical techniques such as linear regression.

But it can also be a biased sample

</br></br>


### Census

Entire population
</br></br>


### Statistical Notation

**Total population**

N

**Sample of population**

n
</br></br>



### Parameter VS. Statistic

**A parameter** is a measure that describes the entire population

**A statistic** is a measure that describes only a sample of a population

[table](https://www.notion.so/dfbd8a117dc147a19b514eb0c555e5e5)

</br></br>


### Describing vs Inferring

Descriptive statistics involve methods of organizing, picturing, and summarizing information from samples and populations

Inferential statistics involves methods of using information from a sample to draw conclusions regarding the population
</br></br>



### Quantitative vs Qualitative data

Quantitative is a numerical measurement of something (continuous)

1. Interval - differences between data values are meaningful

    There is no True zero (it starts anywhere, it ends anywhere)

    example: temperature (in Celsius or Fahrenheit), mark grading, IQ test

2. Ratio - differences between data values are meaningful

    There is a True zero (has a clear definition of 0.0)

    example: heights ( 0 height means nothing).
</br></br>

Qualitative refers to a "quality" or categorical characteristic of something (Categorical)

1. Nominal - Nominal applies to categories, labels or names, and cannot be ordered from smallest to largest

    example: country, gender, race, hair color etc

2. Ordinal - Ordinal applies to data that can be arranged in order in categories

    but the difference between data values cannot be determined or is meaningless

    ordinal data includes having a position in class as “First” or “Second”.

    examples: socio economic status (“low income”,”middle income”,”high income”), education level  (“high school”,”BS”,”MS”,”PhD”)
