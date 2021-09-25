# day210922 - Random Forests Part1

Random Forests combine the simplicity of decision trees with flexibility resulting in a vast improvement in accuracy

**Step 1**: Create a "Bootstrapped" dataset

**Step 2**: Create a decision tree using the bootstrapped dataset, but only use a random subset of variables (or columns) at each step

![Untitled](day210922%20-%20Random%20Forests%20Part1%20db7057b4fb3c42c49d2f3fa54809c8a6/Untitled.png)

![Untitled](day210922%20-%20Random%20Forests%20Part1%20db7057b4fb3c42c49d2f3fa54809c8a6/Untitled%201.png)

Now go back to Step 1 and repeat: Make a new bootstrapped dataset and build a tree considering a subset of variables at each step

The variety is what makes random forests more effective than individual decision trees.

![Untitled](day210922%20-%20Random%20Forests%20Part1%20db7057b4fb3c42c49d2f3fa54809c8a6/Untitled%202.png)

![Untitled](day210922%20-%20Random%20Forests%20Part1%20db7057b4fb3c42c49d2f3fa54809c8a6/Untitled%203.png)

So how are you going to use Random forest then...

1) we get the measurement for one patient. 

2) we run the data down all of the trees we built and we got the result for whether the patient possibly has heart disease.

3) In this case, "Yes" received the most votes, so we will conclude that this patient has heart disease.

**Terminology Alert**

**B**ootstrapping the data plus using the **agg**regate to make a decision is called **Bagging**

**Out of Bag Dataset:** The entries that didn't make it into the bootstrap dataset

Ultimately, we can measure how accurate our random forest is by the proportion of Out-Of-Bag samples that were correctly classified by the Random Forest

1) We select the non-bootstrapped-data and see if it would have been classified correctly in the trees

2) We repeat this process and get the votes for the conclusion 

The proportion of Out-Of-Bag samples that were incorrectly classified is the "**Out-of-Bag Error**"

Since we know how to estimate the Out-Of-Bag-Error, we could optimize how to build the random forest 

In other words... 

1) Build a Random Forest

2) Estimate the accuracy of a Random Forest.

→ change the number of variables used per step

3) do this for a bunch of times and then choose the one that is most accurate.