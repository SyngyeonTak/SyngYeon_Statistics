# day210921 - How to prune Regression Trees

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled.png)

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%201.png)

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%202.png)

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%203.png)

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%204.png)

The main idea behind pruning a Regression Tree is to prevent overfitting the Training Data

So the question is **"How do we decide which tree to use?"**

→ The answer is "**Cost Complexity Pruning**"

### **Cost Complexity Pruning**

The first step in Cost Complexity Pruning is to calculate the **Sum of Squared Residuals** for each tree

**Model 1 (Original Full-size tree)**

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%205.png)

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%206.png)

Now let's calculate the Sum of Squared Residuals for the sub-tree with one fewer leaf.

**Model 2**

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%207.png)

Thus, the total Sum of Squared Residuals for this tree is 320 + 75 + 5099.8 = 5494.8

**So on and So forth**

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%208.png)

Note: The Sum of Squared Residuals is relatively small for the original, full sized tree

But each time we remove a leaf, the Sum of Squared Residuals gets larger and larger

However, we knew that was going to happen because the **whole idea was for the pruned trees to not fit the Training Data** as well as the full sized tree

So... How do we compare these trees?

**Weakest Link Pruning** works by calculating a Tree Score that is based on the **Sum of Squared Residuals (SSR)** for the tree or sub-tree

... and a **Tree Complexity Penalty** that is a function of the number of leaves, or **T**erminal nodes, in the tree or sub-tree

The **Tree Complexity Penalty compensates for the difference in the number of leaves**.

Note: alpha is a tuning parameter that we finding using Cross Validation

$$Tree Score = SSR + aT$$

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%209.png)

Now that we have calculated Tree Scores for all of the trees, we pick the second sub-tree because it has the lowest **Tree Score.** 

Thus, the value for a makes a difference in our choice of sub-tree

### How to build a pruned regression tree

**Use the whole data and build a full-sized Regression Tree (it fits into not just the Training data but also the entire data)**

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%2010.png)

Let's put alpha = 0 here, to remind us that this tree has the lowest Tree Score when alpha = 0

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%2011.png)

In this case, when alpha = 10,000, we'll get a lower Tree Score if we remove these leaves

In the end, different values for alpha give us a sequence of trees, from full-sized to just a leaf

**Now we divide the whole dataset into Training and Testing datasets**

Just using the training data... use the alpha values we found before to build a full tree and a sequence of sub-trees that minimize the Tree Score.

Now calculate the Sum of Squared Residuals for each new tree using only the Testing Data

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%2012.png)

And we go on to the new Training and Testing data

**In training data, we figure out the alpha in accordance with each sub-tree**

**In testing data, we figure out the best alpha by calculating the Sum of Squared Residuals** 

And we just keep repeating until we have done 10-Fold Cross-Validation

Lastly, the value for alpha that, on average, gave us the lowest Sum of Squared Residuals with the Testing Data, is the final value for alpha

In this case, the optimal trees build with a = 10,000 had, on average, the lowest Sum of Squared Residuals.

![Untitled](day210921%20-%20How%20to%20prune%20Regression%20Trees%20b4d86e8860214da69f332d11d7bb0756/Untitled%2013.png)