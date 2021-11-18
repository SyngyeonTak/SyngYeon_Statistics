# day211118 - Neural Networks (Inside the black box) from Statquest

[https://www.youtube.com/watch?v=CqOfi41LfDw&list=PLblh5JKOoLUIxGDQs4LFFD--41Vzf-ME1](https://www.youtube.com/watch?v=CqOfi41LfDw&list=PLblh5JKOoLUIxGDQs4LFFD--41Vzf-ME1)

Neural Networks, one of the most popular algorithms in Machine Learning, cover a broad range of concepts and techniques 

![Untitled](day211118%20-%20Neural%20Networks%20(Inside%20the%20black%20box)%2016b6c41755f447bc9f44a4b0c4c205e2/Untitled.png)

Low / High Dosage is not affected

Only Medium Dosage is under the influence

Imagine that we have to make predictions for the model, We can't simply put a straight line passing through all data. Because now matter how you rotate the line you only could fit into 2 groups, not 3 groups. This is where the neural networks come in. Because we can draw a squiggle line based on the Neural Network. 

![Untitled](day211118%20-%20Neural%20Networks%20(Inside%20the%20black%20box)%2016b6c41755f447bc9f44a4b0c4c205e2/Untitled%201.png)

Before we get into the analysis of the graph and mathematics, let's take a look at the definition of the Neural Network.

Neural Network consists of nodes connecting to each other.

The numbers along each connection represent parameters values that were estimated when this Neural Network was fit to the data

![Untitled](day211118%20-%20Neural%20Networks%20(Inside%20the%20black%20box)%2016b6c41755f447bc9f44a4b0c4c205e2/Untitled%202.png)

For now, just now that these parameters estimates are analogous to the slope and intercept values that we solve for when we fit a straight line to data

![Untitled](day211118%20-%20Neural%20Networks%20(Inside%20the%20black%20box)%2016b6c41755f447bc9f44a4b0c4c205e2/Untitled%203.png)

Also, there are some nodes in the middle of the network that has a curved line inside of them

These bent or curved lines are the building blocks for fitting a squiggle to data

![Untitled](day211118%20-%20Neural%20Networks%20(Inside%20the%20black%20box)%2016b6c41755f447bc9f44a4b0c4c205e2/Untitled%204.png)

The goal is to show you how these identical curves **can be reshaped by the parameter values** and then added together **to get a green squiggle that fits the data**

Terminology

Activation Function: The curved or bent lines

Hidden Layers: The layers of Nodes between the Input and Output nodes 

Step2

So let's see with a simple example. To make the curved line for the hidden layer, we have to figure out what the x-axis coordinate represents. In the example, the dosage multiplied by the parameter value will be on the x-axis coordinate.

To get the corresponding y-axis value, we plug the x value into the Activation Function, which, in this case, is the softplus function 

Here is an important thing. We have to consider how much the input data ranges. It ranges from 0 to 1. Since the range is relatively small, the y value from the hidden layer will be within a small area.

 

![Untitled](day211118%20-%20Neural%20Networks%20(Inside%20the%20black%20box)%2016b6c41755f447bc9f44a4b0c4c205e2/Untitled%205.png)

In other words, when we plug Input values, from 0 to 1, into the Neural Network.  We only get x-axis coordinates that are within the red box. and thus, only the corresponding y-axis values in the red box are used to make this new orange curve. So we see that fitting a Neural Network to data gives us different parameter estimates on the connections. and that results in each Node in the Hidden Layer using different portions of the Activation Functions.