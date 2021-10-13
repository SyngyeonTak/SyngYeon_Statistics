# day211013 - ROC and AUC

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled.png)

If we want to see how to classify we might as well use the probability. Then we set a threshold for classification. let's say we set the threshold at 0.5

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%201.png)

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%202.png)

There are misclassified observations due to the threshold.

and now it is time to look up a confusion matrix

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%203.png)

Now we get to adjust the threshold for the better classification..-

Let's say the threshold is 0.1...

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%204.png)

Then how do we determine which threshold is the best?

It is so confusing if we get every confusion matrix for every threshold(which is not possible)

Instead of being overwhelmed with confusion matrices, Receiver Operator Characteristic(ROC) graphs provide a simple way to summarize all of the information.

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%205.png)

True Positive Rate is

True Positives over True Positives + False Negatives.

The **True Positive Rate** tells you what proportion of obese samples were correctly classified

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%206.png)

The x-axis shows the False Positive Rate, which is the same thing as 1 - Specificity. 

False Positive Rate = (1-Specificity)

False Positives over False Positives plus True Negatives

**The False Positive Rate** tells you the proportion of not obese samples that were incorrectly classified and are False Positives.

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%207.png)

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%208.png)

What does 1, 1 mean?

It means even though we correctly classified all of the obese samples, we incorrectly classified all of the samples that were not obese

![Untitled](day211013%20-%20ROC%20and%20AUC%20bd7a1b253c4a43b58b00ecc1e0d79f4c/Untitled%209.png)

The ROC graph summarizes all of the confusion matrices that each threshold produced

What is AUC?

AUC is the Area Under the Curve

People often replace the False Positive Rate with Precision

Precision is True Positive over True Positive plus False Positive

Precision is the proportion of positive results that were correctly classified

If there were lots of samples that were not obese relative to the number of obese samples, then Precision might be more useful than the False Positive Rate...

Why? Because when the equations for Precision and Recall use both Not obese and Obese class in an equation.

**In summary...**

ROC makes it easier to determine which threshold is the best

AOC visually shows which method is better for the classification(in terms of Sensitivities and Specificities)