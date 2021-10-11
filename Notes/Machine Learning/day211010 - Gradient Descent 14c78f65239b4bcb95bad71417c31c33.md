# day211010 - Gradient Descent

Let's learn how Gradient Descent can fit a line to data by finding the optimal values for the intercept and the Slope

**Predicted Height = intercept + 0.64 * Weight**

We will use Gradient Descent to find the optimal value for the intercept

1. The first thing we do is pick a random value for the Intercept (This is just an initial guess that gives Gradient Descent Something to improve upon.)
2. Now we draw a graph for Sum of squared Residuals(y-axis) and intercept(x-axis)
3. Gradient Descent only does a few calculations far from the optimal solution...
    
    and increases the number of calculations closer to the optimal value
    
    ![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled.png)
    

![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled%201.png)

Now we have an equation for this curve, and we can take the derivative of this function and determine the slope at any value for the intercept

![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled%202.png)

To take the derivative of this, we need to apply the Chain Rule

![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled%203.png)

We start by moving the square to the front

![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled%204.png)

And multiply that by the derivative of the stuff inside the parentheses.

![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled%205.png)

Note: If we were using Least Squares to solve for the optimal value for the Intercept, we would simply find where the slope of the curve = 0

In contrast, **Gradient Descent finds the minimum value by taking steps from an initial guess until it reaches the best value**.

This makes Gradient Descent very **useful when it is not possible to solve for where the derivative = 0**, and this is why Gradient Descent can be used in so many different situations.

![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled%206.png)

This means that when the slope of the curve is close to 0...

Then we should take baby steps because we are close to the optimal value

![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled%207.png)

![Untitled](day211010%20-%20Gradient%20Descent%2014c78f65239b4bcb95bad71417c31c33/Untitled%208.png)

So we know that Gradient Descent has done its job, but without comparing its solution to a gold standard, how does Gradient Descent know to stop taking steps?

→ Gradient Descent stops when the stops Size is very close to 0.

In practice, the Minimum Step Size = 0.001 or smaller. And the Maximum number of steps = 1,000 or greater

Step Size = Slope X Learning Rate

Review So far

The First Thing we did is decide to use **the Sum of the Squared Residuals** as the loss function to evaluate how well a line fits the data.

Then we took the derivatives of the Sum of the Squared Residuals. In other words, we took the derivatives of the **Loss Function**

Then we picked a random value for The Intercept

Then calculated the New Intercept, the difference between the Old Intercept and the Step Size

Lastly, we plugged the New Intercept into the derivative and repeated everything until Step Size was close to 0.

cf: Step Size = Slope X Learning Rate

New Intercept = Old Intercept - Step Size