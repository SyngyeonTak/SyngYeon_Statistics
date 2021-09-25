# day210917 cross-validation digest...

**Intro...**

Definition. Cross-Validation is a statistical method of evaluating and comparing learning algorithms by dividing data into two segments: one used to learn or train a model and the other used to validate the model.

[https://towardsdatascience.com/cross-validation-a-beginners-guide-5b8ca04962cd](https://towardsdatascience.com/cross-validation-a-beginners-guide-5b8ca04962cd)

**Cross Validation: A beginner's Guide**

Cross validation is a form of model validation which attempts to improve on the basic methods of hold-out validation by leveraging subsets of our data and an understanding of the bias/variance trade-off in order to gain a better understanding of how our models will actually perform when applied outside of the data it was trained on.

- **What is model validation?**

    Model validation is the process by which we ensure that our models can perform acceptable in “the real world.” In more technical terms, model validation allows you to predict how your model will perform on datasets not used in the training (model validation is a big part of why preventing data leakage is so important). Model validation is important because we don’t actually care how well the model predicts data we trained it on. We already know the target values for the data we used to train a model, and as such it is much more important to consider how robust and capable a model is when tasked to model new datasets of the same distribution and characteristics, but with different individual values from our training set. The first form of model validation introduced is usually what is known as holdout validation, often considered to be the simplest form of cross validation and thus the easiest to implement. Let’s work through an example below.

    - Holdout validation 1

        For this example, we’ll use a linear regression on the scikit-learn database of California housing data.

        ```python
        # import scikit learn databases
        from sklearn import datasets
        # import california housing data from sklearn and store data into a variable
        calihouses = datasets.fetch_california_housing()
        calidata = calihouses.data
        ```

        Once the data is stored into a variable we can more easily work with, we’ll convert it into a pandas dataframe so we can more easily view and work with the data.

        ```python
        # import pandas and numpy
        import pandas as pd
        import numpy as np
        # define the columns names of the data then convert to dataframe
        headers = calihouses.feature_names
        df = pd.DataFrame(calidata, columns=headers)
        # print the df and shape to get a better understanding of the data
        print(df.shape)
        print(df)
        ```

        Now that we’ve seen the data we’re working with, we can begin the process of generating a model and cross validation. In holdout validation, we split the data into a training and testing set. The training set will be what the model is created on and the testing data will be used to validate the generated model. Though there are (fairly easy) ways to do this using pandas methods, we can make use of scikit-learns “train_test_split” method to accomplish this.

        ```python
        # first store all target data to a variable
        y = calihouses.target
        # create testing and training sets for hold-out verification using scikit learn method
        from sklearn import train_test_split
        X_train, X_test, y_train, y_test = train_test_split(df, y, test_size = 0.25)
        # validate set shapes
        print(X_train.shape, y_train.shape)
        print(X_test.shape, y_test.shape)
        ```

        As you can see, we use the “train_test_split” with three parameters: the input (X) data, the target (y) data, and the percentage of data we’d like to remove and put into the test dataset, in this case 25% (common split is usually 70–30, depending on a multitude of factors about your data). We then assign the split X and y data to a set of new variables to work with later.

    - Holdout validation 2

        Now that we’ve created our test/train split we can create a model and generate some predictions based on the train data. Though there are other methods of creating a model which show more of the nitty gritty, we’ll use scikit learn to make our lives a little easier. I’ve included a few lines to time the runtime of the function, which we will use for later comparison.

        ```python
        # time function using .time methods for later comparison
        from timeit import default_timer as timer
        start_ho = timer()

        # fit a model using linear model method from sklearn
        from sklearn import linear_model
        lm = linear_model.LinearRegression()
        model = lm.fit(X_train, y_train)

        # generate predictions
        predictions = lm.predict(X_test)
        end_ho = timer()

        # calcualte function runtime
        time_ho = (end_ho - start_ho)

        # show predictions
        print(predictions)
        ```

        - **The things to make straight**

            **How does fit function work?**

            Fit function adjusts weights according to data values so that better accuracy can be achieved.

            The fit() method takes the training data as arguments, which can be one array in the case of unsupervised learning, or two arrays in the case of supervised learning. Note that the model is fitted using X and y , but the object holds no reference to X and y .

            **How does predict function work?**

            The predict() function in R is used to predict the values based on the input data.

            predict() : given a trained model, predict the label of a new set of data. This method accepts one argument, the new data X_new (e.g. model. predict(X_new) ), and returns the learned label for each object in the array.

        We’ll start by graphing our given target data vs our predicted target data to give us a visualization of how our model performs.

        ```python
        # import seaborn and plotly
        import matplotlib
        from matplotlib import pyplot as plt
        import seaborn as sns

        # set viz style
        sns.set_style('dark')

        # plot the model
        plot = sns.scatterplot(y_test, predictions)
        plot.set(xlabel='Given', ylabel='Prediction')

        # generate and graph y = x line
        x_plot = np.linspace(0,5,100)
        y_plot = x_plot
        plt.plot(x_plot, y_plot, color='r')
        ```

        ![Untitled](day210917%20cross-validation%20digest%20e2ffd47bac534253b8f5562267f0cdea/Untitled.png)

        In a perfect model (overfit maybe), all our data points would be on that red line, but as our data points approximate that trend, we can see the model is roughly appropriate for the test data.

        ```python
        start_ho_score = timer()

        # model score (neg_mean_squared_error)
        from sklearn import metrics
        # what is metrics???
        # The sklearn. metrics module implements several loss, 
        # score, and utility functions to measure classification performance. 
        # Some metrics might require probability estimates of the positive class
        # , confidence values, or binary decisions values.

        ho_score = -1*metrics.mean_squared_error(y_test, predictions)
        print(ho_score)
        end_ho_score = timer()
        ho_score_time = (end_ho_score - start_ho_score)
        ```

        - **The things to make straight**

            **Mean squared error (MSE)**

            Mean squared error (MSE) is the most commonly used loss function for regression. The loss is the mean overseen data of the squared differences between true and predicted values, or writing it as a formula.

        That’s model validation! We created a model using training data, used it to predict outcomes on a split segment of test data then used a scoring method to determine a measure of effectiveness (negative mean squared error) of the model on the testing data. This gives us an approximation of how well the model will perform on other similar datasets.

        Now, a few things to consider. We validated our model *once*. What if the split we made just happened to be very conducive to this model? What if the split we made introduced a large skew into the date? Didn’t we significantly reduce the size of our training dataset by splitting it like that? These are a few questions we’ll consider as we move into cross validation, but first a few background concepts.

- **What are bias and variance in the context of model validation**

    To understand bias and variance, let’s first address over and under fit models. On overfit model is generated when the model is so tightly fit to the training data that it may account for random noise or unwanted trends which will not be present or useful in predicting targets for subsequent datasets. Underfit occurs when the model is not complex enough to account for general trends in the data which would be useful in predicting targets in subsequent datasets, such as using a linear fit on a polynomial trend

    ![Untitled](day210917%20cross-validation%20digest%20e2ffd47bac534253b8f5562267f0cdea/Untitled%201.png)

    When creating a model, we account for a few types of error: validation error, testing error, error due to bias, and error due to variance in a relationship known as the bias variance trade-off

    - **To make it straight**

        Bias: With one data set, bias means how far the observations are from the linear Regression (for example)

        variance: No matter how the Linear Regression fits into the training data, variance shows how poorly it covers subsequent datasets(test datasets) 

    ![Untitled](day210917%20cross-validation%20digest%20e2ffd47bac534253b8f5562267f0cdea/Untitled%202.png)

    As mentioned earlier, we want to know how the model will perform “in the real world.” Part of that is validation error, which is comprised of error due to bias and error due to variance (training error does not provide information on how the model will perform on future datasets, and can be set aside for now).

    Minimizing model validation error requires finding the point of model complexity where the combination of bias and variance error is minimized, as shown in the linked visual. As model complexity increases, error due to bias decreases, while error due to variance increases, creating the bias-variance trade-off, which we will seek to address later with various methods of cross validation.

    Now let’s define bias and variance:

    **Bias**

    Bias is the error resulting from the difference between the expected value(s) of a model and the actual (or “correct”) value(s) for which we want to predict over multiple iterations. In the scientific concepts of accuracy and precision, bias is very similar to accuracy.

    **Variance**

    Variance is defined as the error resulting from the variability between different data predictions in a model. In variance, the correct value(s) don’t matter as much as the range of differences in value between the predictions. Variance also comes into play more when we run multiple model creation trials.

    ![Untitled](day210917%20cross-validation%20digest%20e2ffd47bac534253b8f5562267f0cdea/Untitled%203.png)

    Variance: How far observation is to each other

    Bias: How far observations are to the target

    In machine learning, bias and variance are often discussed together as a “bias-variance tradeoff,” saying that minimizing one error effectively makes the one more likely to be present when creating and assessing a model. Ideally, we would seek a model whose tradeoff results in both low bias and low variance, and we would look to achieve this by using cross validation. Depending on characteristics of the dataset, one method of cross validation is likely to be more ideal to achieving the bias-variance tradeoff when creating and assessing a model.

- **What is cross validation**

    What if the split we made just happened to be very conducive to this model? What if the split we made introduced a large skew into the date? Didn’t we significantly reduce the size of our training dataset by splitting it like that?

    Cross validation is a method of model validation which splits the data in creative ways in order to obtain the better estimates of “real world” model performance, and minimize validation error.

    **K-Fold Cross Validation**

    K-fold validation is a popular method of cross validation that shuffles the data and splits it into k number of folds (groups). In general K-fold validation is performed by taking one group as the test data set, and the other k-1 groups as the training data, fitting and evaluating a model, and recording the chosen score. This process is then repeated with each fold (group) as the test data and all the scores averaged to obtain a more comprehensive model validation score

    ![Untitled](day210917%20cross-validation%20digest%20e2ffd47bac534253b8f5562267f0cdea/Untitled%204.png)

    When choosing a value for k each fold(group) should be large enough to be representative of the model (commonly k=10 or k=5) and small enough to be computed in a reasonable amount of time. Depending on the dataset size, different k values can sometimes be experimented with. As a general rule, as k increases, bias decreases, and variance increases

    We’ll make use of a linear model again, but this time do model validation with scikit learn’s cross_val_predict method which will do most of the heavy lifting in generating K-Fold predictions. In this case, I chose to set k=10.

    ```python
    # store data as an array
    X = np.array(df)

    # again, timing the function for comparison
    start_kfold = timer()

    # use cross_val_predict to generate K-Fold predictions
    lm_k = linear_model.LinearRegression()
    k_predictions = cross_val_predict(lm_k, X, y, cv=10)
    print(k_predictions)
    end_kfold = timer()
    kfold_time = (end_kfold - start_kfold)
    ```

    ![Untitled](day210917%20cross-validation%20digest%20e2ffd47bac534253b8f5562267f0cdea/Untitled%205.png)

    ‘cross_val_predict’ takes the model used on the data, the input and target data, as well as a ‘cv’ argument — which is essentially our k value — and returns the predicted values for each input. Now we can plot the predictions as we did with the hold out method.

    ```python
    # plot k-fold predictions against actual
    plot_k = sns.scatterplot(y, k_predictions)
    plot_k.set(xlabel='Given', ylabel='Prediction')

    # generate and graph y = x line
    x_plot = np.linspace(0,5,100)
    # The linspace function generates linearly spaced vectors.
    # It is similar to the colon operator ":", but gives direct control 
    # over the number of points. y = linspace(a,b) generates a row vector 
    # y of 100 points linearly spaced between a and b.

    y_plot = x_plot
    plt.plot(x_plot, y_plot, color='r')
    ```

    Now let’s get the scores of the 10 generated models and plot them into a visualization.

    ```python
    kfold_score_start = timer()

    # find the mean score from the k-fold models usinf cross_val_score
    kfold_scores = cross_val_score(lm_k, X, y, cv=10, scoring='neg_mean_squared_error')
    # Why do we even need neg_mean_squared_error
    # This means that a negative value is a prefix to all mse calculations.
    # -1 * mean_squared_error
    # The mse cannot return negative values.
    # Although the difference between one value and the mean can be negative
    # , this negative value is squared. Therefore all results are either positive or zero.

    print(kfold_scores.mean())
    kfold_score_end = timer()
    kfold_score_time = (kfold_score_end - kfold_score_start)

    # plot scores
    sns.distplot(kfold_scores, bins=5)
    ```

    ![Untitled](day210917%20cross-validation%20digest%20e2ffd47bac534253b8f5562267f0cdea/Untitled%206.png)

    You'll notice that the score is a little farther from zero than the holdout method

- **Leave One Out Cross Validation**

    Leave One Out Cross Validation (LOOCV) can be considered a type of K-Fold validation where *k=n* given *n* is the number of rows in the dataset. Other than that the methods are quite similar. You will notice, however, that running the following code will take *much* longer than previous methods. We’ll dig into that later.

    Let’s work an example with the same dataset, following the same process and modifying *k*:

    **Generate predictions:**

    ```python
    start_LOO = timer()

    # generate LOO predictions
    LOO_predictions = cross_val_predict(lm_k, X, y, cv=(len(X)))
    # cv=(len(X)) ->  take n-1 data

    end_LOO = timer()
    LOO_time = (end_LOO - start_LOO)
    ```

    **Plot the predictions**

    ```python
    # plot LOO predictions against actual
    plot_LOO = sns.scatterplot(y, LOO_predictions)
    plot_LOO.set(xlabel='Given', ylabel='Prediction')

    # generate and graph y = x line
    x_plot = np.linspace(0,5,100)
    y_plot = x_plot
    plt.plot(x_plot, y_plot, color='r')
    ```

    **Generate and average scores**

    ```python
    LOO_score_start = timer()

    # find the mean score from the LOO models using cross_val_score 
    LOO_score = cross_val_score(lm_k, X, y, cv=(len(X)), scoring='neg_mean_squared_error').mean()
    print(LOO_score)

    LOO_score_end = timer()
    LOO_score_time = (LOO_score_end - LOO_score_start)
    ```

- **Where, and when should different methods be implemented?**

    **Now lets compare the run times and scores of our three methods**

    ```python
    print("Hold out method took"
    	, time_ho
    	, "seconds to generate a model and"
    	, ho_score_time ,"seconds to generate a MSE of", ho_score)

    print("K-Fold method took"
    	, kfold_time
    	, 'seconds to generate a model and'
    	, kfold_score_time
    	, 'seconds to generate a MSE of'
    	, kfold_scores.mean())

    print("Leave One Out Cross Validation method took"
    	, LOO_time
    	, 'seconds to generate a model and'
    	, LOO_score_time
    	, 'seconds to generate a MSE of'
    	, LOO_score)

    /*
    output

    Hold out method took
     0.03958953900000495
    seconds to generate a model and 0.002666198000042641
    seconds to generate a MSE of -0.5201754311947533

    K-Fold method took
     0.07809067700000583 
    seconds to generate a model and 0.1253743699999177 
    seconds to generate a MSE of -0.5509524296956634

    Leave One Out Cross Validation method took 
     152.00629317099992 
    seconds to generate a model and 161.83364986200013 
    seconds to generate a MSE of -0.5282462043712458
    */
    ```

    As we noticed in the results of our comparison, we can see that the LOOCV method takes **way** longer to complete than our other two. This is because that method creates and evaluates a model for each row in the dataset, in this case over 20,000. Even though our MSE is a little lower, this may not be worth it given the additional computational requirements. Here are some heuristics which can help in choosing a method.

    **Hold out method**

    The hold out method can be effective and computationally inexpensive on very large datasets, or on limited computational resources. It is also often easier to implement and understand for beginners. However, it is very rarely good to apply to small datasets as it can significantly reduce the training data available and hurt model performance.

    **K-Fold Cross Validation**

    K-Fold can be very effective on medium sized datasets, though by adjusting the K value can significantly alter the results of the validation. Let’s add to our rule from earlier; as k increases, bias decreases, and variance and computational requirements increase. K-Fold cross validation is likely the most common of the three methods due to the versatility of adjusting K-values.

    **LOOCV**

    LOOCV is most useful in small datasets as it allows for the smallest amount of data to be removed from the training data in each iteration. However, in large datasets the process of generating a model for each row in the dataset can be incredibly computationally expensive and thus prohibitive for larger datasets.

    ### **What are some advantages and disadvantages of the different cross validation techniques?**

    **Holdout Validation**

    In holdout validation, we are doing nothing more than performing a simple train/test split in which we fit our model to our training data and apply it to our testing data to generate predicted values. We “hold out” the testing data to be strictly used for prediction purposes only. Holdout validation is NOT a cross validation technique. But we must discuss the standard method of model evaluation so that we can compare its attributes with the actual cross validation techniques.

    When it comes to code, holdout validation is easy to use. The implementation is simple and doesn’t require large dedications to computational power and time complexity. Moreover, we can interpret and understand the results of holdout validation better as they don’t require us to figure out how the iterations are performing in the grand scheme of things.

    However, holdout validation does not preserve the statistical integrity of the dataset in many cases. For instance, a holdout validation that splits the data into training and testing segments causes bias by not incorporating the testing data into the model. The testing data could contain some important observations. This would result in a detriment to the accuracy of the model. Furthermore, this will cause an underfitting and overfitting of the data in addition to an introduction of validation and/or training error.

    **K-fold**

    In K-fold cross validation, we answer many of the problems inherent in holdout validation such as underfitting/overfitting and validation and training error. This is done by using all of the observations in our validation set at some iteration. We compute an average accuracy score of all the accuracy scores that are calculated in each k iteration. By doing so, we minimize bias and variation that may be present in our initial model evaluation technique, holdout validation.  However, in terms of computational power, k-fold cross validation is very costly. The computer has to perform several iterations to generate a proper accuracy score. The accuracy score of the model will in theory increase with each added k iteration. This will decrease bias while increasing variation. We will see an example of this later in this article when we attempt to apply k-fold validation to a very large dataset that contains about 580,000 observations.

    **LOOCV**

    LOOCV is very similar to K-fold, with a special case in which k is equal to the length (or number of samples/rows) of the whole dataset. Thus the training set will be of length k-1, and the testing set will be a single sample of the data. LOOCV is particularly useful in the case that our data set is not large enough to sensibly do Kfold. LOOCV is also less computationally expensive in general, although it is usually due to the inherently smaller datasets that tend to utilize it.

    However, LOOCV tends to yield high variance due to the fact that the method would pick up on all of the possible noise and outlier values in the data through the individual testing values. LOOCV would be very computationally expensive for very large data sets; in this case, it would be better to use regular k-fold.

    ### **When would you not want to use cross validation?**

    Cross validation becomes a computationally expensive and taxing method of model evaluation when dealing with large datasets. Generating prediction values ends up taking a very long time because the validation method have to run k times in K-Fold strategy, iterating through the entire dataset. Thus cross validation becomes a very costly model evaluation strategy in terms of time complexity. We will examine this phenomenon by performing a normal holdout validation and a K-Fold cross validation on a very large dataset with approximately 580,000 rows. See if you can figure it out, why it works the way it does (and the new data visualizations), and comment any questions. Good luck!

    ```python
    # upload dataset from kaggle (we're using google colab here, adapt to your IDE)
    from google.colab import files
    uploaded = files.upload()

    # initialize data frame
    df = pd.read_csv("covtype.csv")
    print(df.head())
    print(df.tail())

    # that's a lot of rows!
    # notice that we use all features of our dataset 
    # so that we can illustrate how taxing cross validation will be
    X=df.loc[:,'Elevation':'Soil_Type40']
    y=df['Cover_Type']

    # some nan values happen to sneak into our dataset so we will fill them up
    X = X.fillna(method='ffill')
    y = y.fillna(method='ffill')

    # use a K-nearest neighbhors machine learning algorithm
    neigh = KNeighborsClassifier(n_neighbors=5)

    # only with 200 folds are we able to generate an accuracy of 80%
    neigh.fit(X,y)
    kFoldStart = time.time()
    y_pred = cross_val_predict(neigh, X, y, cv = 200)
    kFoldEnd = time.time()
    kFoldTime = kFoldEnd - kFoldStart
    print("K Fold Validation Accuracy is ", accuracy_score(y, y_pred))

    # it takes 16 minutes to run the K-Fold cross validation!!!!
    print(kFoldTime)
    ```