# day210930 - Feature importance

[https://machinelearningmastery.com/calculate-feature-importance-with-python/](https://machinelearningmastery.com/calculate-feature-importance-with-python/)

**Feature importance** refers to techniques that assign a score to input features based on how useful they are at predicting a target variable.

There are many types and sources of feature importance scores, although popular examples include statistical correlation scores, coefficients calculated as part of linear models, decision trees, and permutation importance scores.

Feature importance scores play an important role in a predictive modeling project, including providing insight into the data, insight into the model, and the basis for [dimensionality reduction](https://machinelearningmastery.com/dimensionality-reduction-for-machine-learning/) and [feature selection](https://machinelearningmastery.com/rfe-feature-selection-in-python/) that can improve the efficiency and effectiveness of a predictive model on the problem.

In this tutorial, you will discover feature importance scores for machine learning in python

After completing this tutorial, you will know:

- The role of feature importance in a predictive modeling problem.
- How to calculate and review feature importance from linear models and decision trees.
- How to calculate and review permutation feature importance scores.

- **Feature Importance**
    
    Feature importance refers to a class of techniques for assigning scores to input features to a predictive model that indicates the relative importance of each feature when making a prediction.
    
    Feature importance scores can be calculated for problems that involve predicting a numerical value, called regression, and those problems that involve predicting a class label, called classification.
    
    The scores are useful and can be used in a range of situations in a predictive modeling problem, such as:
    
    - Better understanding the data.
    - Better understanding a model.
    - Reducing the number of input features.
    
    **Feature importance scores can provide insight into the dataset**. The relative scores can highlight which features may be most relevant to the target, and the converse, which features are the least relevant. This may be interpreted by a domain expert and could be used as the basis for gathering more or different data.
    
    **Feature importance scores can provide insight into the model**. Most importance scores are calculated by a predictive model that has been fit on the dataset. Inspecting the importance score provides insight into that specific model and which features are the most important and least important to the model when making a prediction. This is a type of model interpretation that can be performed for those models that support it.
    
    **Feature importance can be used to improve a predictive model**. This can be achieved by using the importance scores to select those features to delete (lowest scores) or those features to keep (highest scores). This is a type of feature selection and can simplify the problem that is being modeled, speed up the modeling process (deleting features is called dimensionality reduction), and in some cases, improve the performance of the model.
    
    > Often, we desire to quantify the strength of the relationship between the predictors and the outcome. […] Ranking predictors in this manner can be very useful when sifting through large amounts of data.
    > 
    
    Feature importance scores can be fed to a wrapper model, such as the [SelectFromModel](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectFromModel.html) class, to perform feature selection.
    
    There are many ways to calculate feature importance scores and many models that can be used for this purpose.
    
    Perhaps the simplest way is to calculate simple coefficient statistics between each feature and the target variable. For more on this approach, see the tutorial:
    
    - [How to Choose a Feature Selection Method for Machine Learning](https://machinelearningmastery.com/feature-selection-with-real-and-categorical-data/)
    
    In this tutorial, we will look at three main types of more advanced feature importance; they are:
    
    - Feature importance from model coefficients.
    - Feature importance from decision trees.
    - Feature importance from permutation testing.
    
    Let’s take a closer look at each.
    

- **Preparation**
    
    Before we dive in, let’s confirm our environment and prepare some test datasets.
    
    ### **Check Scikit-Learn Version**
    
    First, confirm that you have a modern version of the scikit-learn library installed.
    
    This is important because some of the models we will explore in this tutorial require a modern version of the library.
    
    You can check the version of the library you have installed with the following code example:
    
    ```python
    # check scikit-learn version
    import sklearn
    print(sklearn.__version__)
    ```
    
    ### **Test Datasets**
    
    Next, let’s define some test datasets that we can use as the basis for demonstrating and exploring feature importance scores.
    
    Each test problem has five important and five unimportant features, and it may be interesting to see which methods are consistent at finding or differentiating the features based on their importance.
    
    ### **Classification Dataset**
    
    We will use the make_classification() function to create a test binary classification dataset.
    
    The dataset will have 1,000 examples, with 10 input features, five of which will be informative and the remaining five will be redundant. We will fix the random number seed to ensure we get the same examples each time the code is run.
    
    An example of creating and summarizing the dataset is listed below.
    
    When it comes to the construction for make_classification, it needs parameters.
    
    - n_features : The total number of features
    - n_informative : The number of related features.
    - n_redundant : The number of unrelated features
    
    ```python
    # test classification dataset
    from sklearn.datasets import make_classification
    
    # define dataset
    X, y = make_classification(n_smaples = 1000, n_features = 10, n_informative = 5, n_redundant = 5))
    
    # summarize the dataset
    print(X.shape, y.shape)
    #-> (1000, 10) (1000,)
    ```
    

- **Coefficients as Feature Importance**
    
    Linear machine learning algorithms fit a model where the prediction is **the weighted sum of the input values**.
    
    Examples include linear regression, logistic regression, and extensions that add regularization, such as ridge regression and the elastic net.
    
    All of these algorithms find a set of coefficients to use in the weighted sum in order to make a prediction. These coefficients can **be used directly as a crude type of feature importance score**. Let’s take a closer look at using coefficients as feature importance for classification and regression. We will fit a model on the dataset to find the coefficients, then summarize the importance scores for each input feature and finally create a bar chart to get an idea of the relative importance of the features.
    

- **Linear Regression Feature Importance**
    
    We can fit a LinearRegression model on the regression dataset and retrieve the *coeff_* property that contains the coefficients found for each input variable.
    
    **These coefficients can provide the basis for a crude feature importance score**. This assumes that **the input variables have the same scale** or have been scaled prior to fitting a model.
    
    The complete example of linear regression coefficients for feature importance is listed below.
    
    ```python
    # linear regression feature importance
    from sklearn.datasets import make_regression
    from sklearn.linear_model import LinearRegression
    from matplotlib import pyplot
    
    # define dataset
    X, y = make_regression(n_samples = 1000
    				, n_features = 10
    				, n_inforamtive = 5
    				, random_state = 1)
    
    # define the model
    model = LinearRegression()
    
    # fit the model
    model.fit(X, y)
    
    # get importance
    importance = model.coef_
    # LinearRegression.coef = Estimated coefficients for the linear regression problem.
    # If multiple targets are passed during the fit (y 2D),
    # this is a 2D array of shape (n_targets, n_features),
    # while if only one target is passed, this is a 1D array of length n_features.
    
    # summarize feature importance
    for i, v in enumerate(importance):
    	print('Feature: %0d, Score: %5.f' % (i, v))
    
    # plot feature importance
    pyplot.bar([x for x in range(len(importance))], importance)
    pyplot.show()
    ```
    

- **Logistic Regression Feature Importance**
    
    We can fit a [LogisticRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) model on the regression dataset and retrieve the *coeff_* property that **contains the coefficients found for each input variable.**
    
    These coefficients can **provide the basis for a crude feature importance score**. This assumes that the input variables have the same scale or have been scaled **prior to fitting a model**.
    
    The complete example of logistic regression coefficients for feature importance is listed below.
    
    ```python
    # logistic regression for feature importance
    from sklearn.datasets import make_classification
    from sklearn.linear_model import LogisticRegression
    from matplotlib import pyplot
    
    # define dataset
    X, y = make_classification(n_samples = 1000
    					, n_features = 10
    					, n_informative = 5
    					, n_redundant = 5
    					, random_state = 1)
    
    # define the model
    model = LogisticRegression()
    
    # fit the model
    model.fit(X, y)
    
    # get importance
    importance = model.coef_[0]
    
    # summarize feature importance
    for i, v enumberate(importance):
    	print('Feature: %0d, Score: %.5f' % (i, v))
    
    # plot feature importance
    pyplot.bar([x for x in range(len(importance))], importance)
    pyplot.show()
    ```
    
    Running the example fits the model, then reports the coefficient value for each feature.
    
    **Note**: Your [results may vary](https://machinelearningmastery.com/different-results-each-time-in-machine-learning/) given the stochastic nature of the algorithm or evaluation procedure, or differences in numerical precision. Consider running the example a few times and compare the average outcome.
    
    Recall this is a classification problem with classes 0 and 1. Notice that the coefficients are both positive and negative. The positive scores indicate a feature that predicts class 1, whereas the negative scores indicate a feature that predicts class 0.
    
    No clear pattern of important and unimportant features can be identified from these results, at least from what I can tell.
    

- **Decision Tree Feature Importance**
    
    Decision tree algorithms like [classification and regression trees](https://machinelearningmastery.com/implement-decision-tree-algorithm-scratch-python/) (CART) offer importance scores based on the reduction in the criterion used to select split points, like Gini or entropy.
    
    This same approach can be used for ensembles of decision trees, such as the random forest and stochastic gradient boosting algorithms.
    
    Let’s take a look at a worked example of each.