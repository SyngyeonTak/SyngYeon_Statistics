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