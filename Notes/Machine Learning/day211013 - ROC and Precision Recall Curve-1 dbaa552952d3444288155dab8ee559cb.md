# day211013 - ROC and Precision Recall Curve-1

[https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_curve.html](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_curve.html)

- From API
    
    **Compute precision-recall pairs for different probability thresholds.**
    
    Note: this implementation is **restricted to the binary classification task**.
    
    The precision is the ratio `tp / (tp + fp)` where `tp` is the number of true positives and `fp` the number of false positives. The precision is intuitively **the ability of the classifier** not to label as positive a sample that is negative.
    
    The recall is the ratio `tp / (tp + fn)` where `tp` is the number of true positives and `fn` the number of false negatives. The recall is intuitively **the ability of the classifier to find all the positive samples.**
    
    The last precision and recall values are 1. and 0. respectively and do not have a corresponding threshold. This ensures that the graph starts on the y axis.
    

[https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/](https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/)

- **How to Use ROC Curves and Precision-Recall Curves for Classification in Python**
    
    It can be more flexible to **predict probabilities of an observation belonging to each class in a classification problem rather than predicting classes directly.**
    
    **This flexibility comes from the way that probabilities may be interpreted using different thresholds** that allow the operator of the model **to trade-off concerns in the errors** made by the model, **such as the number of false positives compared to the number of false negatives.** **This is required when using models where the cost of one error outweighs the cost of other types of errors.**
    
    Two diagnostic tools that help in the interpretation of probabilistic forecast for binary (two-class) classification predictive modeling problems are **ROC Curves** and **Precision-Recall curves**.
    
    In this tutorial, you will discover ROC Curves, Precision-Recall Curves, and when to use each to interpret the prediction of probabilities for binary classification problems.
    

- **Predicting Probabilities**
    
    In a classification problem, we may decide to predict the class values directly.
    
    Alternately, **it can be more flexible to predict the probabilities for each class instead**. The reason for this is to provide the capability to choose and even calibrate **the threshold for how to interpret the predicted probabilities.**
    
    For example, a default might be to use a threshold of 0.5, meaning that a probability in [0.0, 0.49] is a negative outcome (0) and a probability in [0.5, 1.0] is a positive outcome (1).
    
    This threshold can be adjusted to tune the behavior of the model for a specific problem. An example would be to reduce more of one or another type of error.
    
    When making a prediction for a binary or two-class classification problem, there are two types of errors that we could make.
    
    - **False Positive**. Predict an event when there was no event.
    - **False Negative**. Predict no event when in fact there was an event.
    
    By predicting probabilities and calibrating a threshold, a balance of these two concerns can be chosen by the operator of the model.
    
    For example, in a smog prediction system, we may be far more concerned with having low false negatives than low false positives. A false negative would mean not warning about a smog day when in fact it is a high smog day, leading to health issues in the public that are unable to take precautions. A false positive means the public would take precautionary measures when they didn’t need to.
    
    A common way to compare models that predict probabilities for two-class problems is to use a ROC curve.