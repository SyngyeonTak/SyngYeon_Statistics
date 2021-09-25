# day210911 - Support Vector Machines

![Untitled](day210911%20-%20Support%20Vector%20Machines%207a391057e0fb470f88c0e608b226f5b5/Untitled.png)

The x-axis coordinates in this graph will be the dosages that we have already observed

and y-axis coordinates will be the square of the dosages (Dosage^2)

![Untitled](day210911%20-%20Support%20Vector%20Machines%207a391057e0fb470f88c0e608b226f5b5/Untitled%201.png)

Since each observation has x and y-axis coordinates, the data are now 2-dimensional

And now that the data are 2-dimensional, we can draw a Support Vector Classifier that separates the people who were cured from the people who were not cured.

**The main ideas behind Support Vector Machines are...**

1) Start with data in a relatively low dimension(1 dimension)

2) Move the data into a higher dimension(1 dimension → 2 dimension)

3) Find a Support Vector Classifier that separates the higher dimensional data into two groups

**How do we decide how to transform the data?**
In order to make the mathematics possible, Support Vector Machines use something called Kernel Functions to systematically find Support Vector Classifiers in higher dimensions.

### Polynomial Kernel

For this example, I used the Polynomial Kernel, which has a parameter, d, which stands for the degree of the polynomial

When d = 1, the Polynomial Kernel computes the relationships between each pair of observations in 1-Dimension

And these relationships are used to find a Support Vector Classifier

When d = 2, we get a 2nd dimension based on Dosages^2

![Untitled](day210911%20-%20Support%20Vector%20Machines%207a391057e0fb470f88c0e608b226f5b5/Untitled%202.png)

In summary, the Polynomial Kernel systematically increases dimensions by setting d, the degree of the polynomial and the relationships between each pair of observations are used to find a Support Vector Classifier

### Radial Kernel

Unfortunately, the Radial Kernel finds Support Vector Classifiers in infinite dimensions, so I can't give you an example of what it does exactly.

![Untitled](day210911%20-%20Support%20Vector%20Machines%207a391057e0fb470f88c0e608b226f5b5/Untitled%203.png)

The Radial Kernel behaves like a Weighted Nearest Neighbor model

In other words, the closest observations (the nearest neighbors) have a lot of influence on how we classify the new observation.

and observations further away have relatively little influence on the classification

![Untitled](day210911%20-%20Support%20Vector%20Machines%207a391057e0fb470f88c0e608b226f5b5/Untitled%204.png)

The Radial Kernel uses their classification for the new observation

**To make things straight**

Kernel functions only calculate the relationships between every pair of points as if they are in the higher dimensions; they don't actually do the transformation

This trick, calculating the high-dimensional relationships without actually transforming the data to the higher dimension, is called The Kernel Trick

**In a nutshell**

Finding a relatively high dimensional Support Vector Classifier that can effectively classify the observations.