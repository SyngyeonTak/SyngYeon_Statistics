# day211020 - How to know if your machine learning model has good performance

[https://machinelearningmastery.com/how-to-know-if-your-machine-learning-model-has-good-performance/](https://machinelearningmastery.com/how-to-know-if-your-machine-learning-model-has-good-performance/)

After reading this post, you will know:

- That a baseline model can be used to discover the bedrock in performance on your problem by which all other models can be evaluated.
- That all predictive models contain errors and that a perfect score is not possible in practice given the stochastic nature of data and algorithms.
- That the true job of applied machine learning is to explore the space of possible models and discover what a good model score looks like relative to the baseline on your specific dataset.

# **Overview**

This post is divided into 4 parts; they are:

1. Model Skill Is Relative
2. Baseline Model Skill
3. What Is the Best Score?
4. Discover Limits of Model Skill

# **Model Skill Is Relative**

Your predictive modeling problem is unique.

This includes the specific data you have, the tools you’re using, and the skill you will achieve.

Your predictive modeling problem has not been solved before. Therefore, we cannot know what a good model looks like or what skill it might have.

You may have ideas of what a skillful model looks like based on knowledge of the domain, but you don’t know whether those skill scores are achievable.

The best that we can do is to compare the performance of machine learning models on your specific data to other models also trained on the same data.

Machine learning model performance is relative and ideas of what score a good model can achieve only make sense and can only be interpreted in the context of the skill scores of other models also trained on the same data.

# **Baseline Model Skill**

Because machine learning model performance is relative, it is critical to develop a robust baseline.

A baseline is a simple and well understood procedure for making predictions on your predictive modeling problem. The skill of this model provides the bedrock for the lowest acceptable performance of a machine learning model on your specific dataset.

The results for the baseline model provide the point from which the skill of all other models trained on your data can be evaluated.

Three examples of baseline models include:

- Predict the mean outcome value for a regression problem.
- Predict the mode outcome value for a classification problem.
- Predict the input as the output (called persistence) for a univariate time series forecasting problem.

The baseline performance on your problem can then be used as the yardstick by which all other models can be compared and evaluated.

If a model achieves a performance below the baseline, something is wrong (e.g. there’s a bug) or the model is not appropriate for your problem.

# **What Is the Best Score?**

If you are working on a classification problem, the best score is 100% accuracy.

If you are working on a regression problem, the best score is 0.0 error.

These scores are an impossible to achieve upper/lower bound. All predictive modeling problems have prediction error. Expect it. The error comes from a range of sources such as:

- Incompleteness of data sample.
- Noise in the data.
- Stochastic nature of the modeling algorithm.

You cannot achieve the best score, but it is good to know what the best possible performance is for your chosen measure. You know that true model performance will fall within a range between the baseline and the best possible score.

Instead, you must search the space of possible models on your dataset and discover what good and bad scores look like.

# **Discover Limits of Model Skill**

Once you have the baseline, you can explore the extent of model performance on your predictive modeling problem.

In fact, this is the hard work and the objective of the project: to find a model that you can demonstrate works reliably well in making predictions on your specific dataset.

There are many strategies to this problem; two that you may wish to consider are:

- **Start High**. Select a machine learning method that is sophisticated and known to perform well on a range of predictive model problems, such as random forest or gradient boosting. Evaluate the model on your problem and use the result as an approximate top-end benchmark, then find the simplest model that achieves similar performance.
- **Exhaustive Search**. Evaluate all of the machine learning methods that you can think of on the problem and select the method that achieves the best performance relative to the baseline.

The “*Start High*” approach is fast and can help you define the bounds of model skill to expect on the problem and find a simple (e.g. Occam’s Razor) model that can achieve similar results. It can also help you find out whether the problem is solvable/predictable fast, which is important because not all problems are predictable.

The “*Exhaustive Search*” is slow and is really intended for long-running projects where model skill is more important than almost any other concern. I often perform variations of this approach testing suites of similar methods in batches and call it the [spot-checking](https://machinelearningmastery.com/why-you-should-be-spot-checking-algorithms-on-your-machine-learning-problems/) approach.

Both methods will give you a population of model performance scores that you can compare to the baseline.

You will know what a good score looks like and what a bad score looks like.