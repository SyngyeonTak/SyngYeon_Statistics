# day211018 - Gradient Boost (statquest 1 , 2) - Regression

**Gradient Boost - Linear Regression**

  Note: When Gradient Boost is used to predict a continuous value, like Weight, we say that we are using Gradient Boost for Regression

Using Gradient Boost for Regression is different from doing Linear Regression, so while the two methods are related, don't get them confused with each other

**Let's briefly compare and contrast AdaBoost and Gradient Boost**

AdaBoost starts by building a very short tree, called a **Stump**, from the Training Data 

And the amount of say that the stump has on **the final output is based on how well it compensated for those previous errors**

In contrast, Gradient Boost starts by making a single leaf, instead of a tree or stump

This leaf represents an initial guess for the Weights of all of the samples

The first value is the average value

The more you run the model, the larger the tree gets.

But usually the **maximum number of leaves to be between 8 and 32**

**Gradient Boost scales all trees by the same amount**

Then Gradient Boost builds another tree based on the errors made by the previous tree

**Let's get into how the Gradient Boost works**

1. Let's say we have to predict the continuous value. For starters, we have to get the average of the whole observed values. And we get... (Observed Value - Average(Predicted)) the value from that subtraction is called Pseudo Residual.
2. The predicted value comes from subtraction from the value of a leave and the previous predicted value. But it leads to too well fitting value(over fitting). So we need something to scale the predicted value, Learning Rate.
3. We get the pseudo value of the next batch. And we keep scaling the trees by the Learning rate. We get The average + (learning scale * first residual) + (learning scale * second  residual)... It goes toward making a good prediciton

**Let's dive into the regression equation...**

![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled.png)

- **Input: data and a differentiable Loss Function**
    
    ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%201.png)
    
    This line describes, in an abstract way, the Training dataset, and the method we will use to evaluate how well the model fits the Training Dataset
    
    Don't freak out from how the equation looks. It is just how it looks in a fancy way that we have the data frame above
    
    The **xi** refers to **each row of measurements** that we will use to predict Weight
    
    The **yi** refers to the **Weights measured (Target Variable)** for each person in the dataset
    
    This part just says that the i's go from 1 to n, where n is the number of people in our dataset
    
    The Loss Function that is most commonly used when doing Regression with Gradient Boost is 
    
    1/2(observed - Predicted ) Squared
    
    Note: The reason why we get a half for the Squared Residuals is that we need to use the chain rule for the equation.
    
    Why do we have to use derivatives? Because we have to see Squared of Residuals with respect to Predicted value
    
    ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%202.png)
    
    the yi is the value of Weight
    
    F(x) is the function that gets a predicted value
    

- **Step 1: Initialize model with a constant value**
    
    ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%203.png)
    
    The equation on the right side is the Loss Function. Which goes like this below...
    
    ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%204.png)
    
    "**argmin over gamma**" means we need to find **a Predicted value that minimizes this sum**
    
     In other words, if we plot the Observed Weights on a number line 
    
    ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%205.png)
    
    Here's a plot of one half of the sum of the squared residuals for potential predicted values
    
    ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%206.png)
    
    We found out that the average minimizes the sum of Squared Residuals 
    
    ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%207.png)
    
    That means that the initial predicted value, F0(x), is just a leaf
    

- **Step 2: for m = 1 to M**
    
    Step 2 is just a loop where we make all of the trees. We are gonna plug 100 into M
    
    Little m refers to an individual tree.
    
    - **(A)**
        
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%208.png)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%209.png)
        
        With respect to the predicted value
        
        That leaves us (Observed - Predicted), just a Residual
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2010.png)
        
        At the first iteration, we get the average of the observed values
        
        → (Observed - 73.3)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2011.png)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2012.png)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2013.png)
        
    - **(B)**
        
        **(B) Fit a regression tree to the rim values and create terminal regions Rjm, for j = 1... Jm**
        
        All this is saying is that we will build a regression tree...
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2014.png)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2015.png)
        
    - **(C)**
        
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2016.png)
        
        In this part, we determine the Output values for each leaf.
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2017.png)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2018.png)
        
        The equation in the red box is just what we did for (A), while this one takes the previous prediction into account 
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2019.png)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2020.png)
        
        Then only x of 3 is used to calculate the output value for R1,1
        
        Since only x of 3 goes to R 1,1, expanding means we remove the big sigma and swap the i's with 3's.
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2021.png)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2022.png)
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2023.png)
        
        Then only x1 and x2 are used to calculate the Output value for R1,2.
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2024.png)
        
        Note
        
        Given our choice of Loss Function the Output Values are always the average of the Residuals that end up in the same leaf
        
    - **(D)**
        
        **(D) In part D, we make a new prediction for each sample.**
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2025.png)
        
        Note: This summation is there just in case a single sample ends up in multiple leaves
        
        The summation says we should add up the Output Values, gamma j,m's for all the leaves, R j,m that a sample, x, can be found in
        
        The last thing in this equation is this Greek character "nu"
        
        Nu is the Learning Rate, and is a value between 1 and 0
        
        A small Learning Rate reduces the effect each tree has on the final prediction, and this improves accuracy in the long run 
        
        ![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2026.png)
        

**Just an overview...**

![Untitled](day211018%20-%20Gradient%20Boost%20(statquest%201%20,%202)%20-%20Reg%20ea631602d65f40bb863afff5cab9fa37/Untitled%2027.png)