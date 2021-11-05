# day211105 - What is the random_state and shuffle

[https://machinelearningmastery.com/k-fold-cross-validation/](https://machinelearningmastery.com/k-fold-cross-validation/)

The general procedure is as follows:

1. Shuffle the dataset randomly.
2. Split the dataset into k groups
3. For each unique group:
    1. Take the group as a hold out or test data set
    2. Take the remaining groups as a training data set
    3. Fit a model on the training set and evaluate it on the test set
    4. Retain the evaluation score and discard the model
4. Summarize the skill of the model using the sample of model evaluation scores

Importantly, each observation in the data sample is assigned to an individual group and stays in that group for the duration of the procedure. This means that each sample is given the opportunity to be used in the hold out set 1 time and used to train the model k-1 times.

It is also important that any preparation of the data prior to fitting the model occur on the CV-assigned training dataset within the loop rather than on the broader data set. This also applies to any tuning of hyperparameters. A failure to perform these operations within the loop may result in [data leakage](https://machinelearningmastery.com/data-leakage-machine-learning/) and an optimistic estimate of the model skill.

# **Cross-Validation API**

We do not have to implement k-fold cross-validation manually. The scikit-learn library provides an implementation that will split a given data sample up.

The *KFold()* scikit-learn class can be used. It takes as arguments the number of splits, whether or not to shuffle the sample, and the seed for the [pseudorandom number generator](https://machinelearningmastery.com/how-to-generate-random-numbers-in-python/) used prior to the shuffle.

For example, we can create an instance that splits a dataset into 3 folds, shuffles prior to the split, and uses a value of 1 for the pseudorandom number generator.

```python
**kfold = KFold(3, True, 1)**
```

The *split()* function can then be called on the class where the data sample is provided as an argument. Called repeatedly, the split will return each group of train and test sets. Specifically, arrays are returned containing the indexes into the original data sample of observations to use for train and test sets on each iteration.

For example, we can enumerate the splits of the indices for a data sample using the created *KFold* instance as follows:

```python
**# enumerate splits
for train, test in kfold.split(data):	
	print('train: %s, test: %s' % (train, test))**
```

We can tie all of this together with our small dataset used in the worked example of the prior section.

```python
**# scikit-learn k-fold cross-validation
from numpy import array
from sklearn.model_selection import KFold
# data sample
data = array([0.1, 0.2, 0.3, 0.4, 0.5, 0.6])
# prepare cross validation
kfold = KFold(3, True, 1)
# enumerate splits
for train, test in kfold.split(data):
	 print('train: %s, test: %s' % (data[train], data[test]))**
```

Running the example prints the specific observations chosen for each train and test set. The indices are used directly on the original data array to retrieve the observation values.

```python
**train: [0.1 0.4 0.5 0.6], test: [0.2 0.3]
train: [0.2 0.3 0.4 0.6], test: [0.1 0.5]
train: [0.1 0.2 0.3 0.5], test: [0.4 0.6]**
```

Usefully, the k-fold cross validation implementation in scikit-learn is provided as a component operation within broader methods, such as grid-searching model hyperparameters and scoring a model on a dataset.

Nevertheless, the *KFold* class can be used directly in order to split up a dataset prior to modeling such that all models will use the same data splits. This is especially helpful if you are working with very large data samples. The use of the same splits across algorithms can have benefits for statistical tests that you may wish to perform on the data later.

# **Variations on Cross-Validation**

There are a number of variations on the k-fold cross validation procedure.

Three commonly used variations are as follows:

- **Train/Test Split**: Taken to one extreme, k may be set to 2 (not 1) such that a single [train/test split](https://machinelearningmastery.com/train-test-split-for-evaluating-machine-learning-algorithms/) is created to evaluate the model.
- **LOOCV**: Taken to another extreme, k may be set to the total number of observations in the dataset such that each observation is given a chance to be the held out of the dataset. This is called leave-one-out cross-validation, or [LOOCV](https://machinelearningmastery.com/loocv-for-evaluating-machine-learning-algorithms/) for short.
- **Stratified**: The splitting of data into folds may be governed by criteria such as ensuring that each fold has the same proportion of observations with a given categorical value, such as the class outcome value. This is called [stratified cross-validation](https://machinelearningmastery.com/cross-validation-for-imbalanced-classification/).
- **Repeated**: This is where the k-fold cross-validation procedure is [repeated n times](https://machinelearningmastery.com/repeated-k-fold-cross-validation-with-python/), where importantly, the data sample is shuffled prior to each repetition, which results in a different split of the sample.
- **Nested**: This is where k-fold cross-validation is performed within each fold of cross-validation, often to perform hyperparameter tuning during model evaluation. This is called [nested cross-validation](https://machinelearningmastery.com/nested-cross-validation-for-machine-learning-with-python/) or double cross-validation.