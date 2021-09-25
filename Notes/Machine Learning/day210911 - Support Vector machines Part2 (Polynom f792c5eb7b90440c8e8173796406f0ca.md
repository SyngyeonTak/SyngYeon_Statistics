# day210911 -  Support Vector machines Part2 (Polynomial Kernel)

Specifically, we're going to talk about the Polynomial Kernel's parameters...

**Polynomial Kernel**

$(a * b + r)^d$

talk about how the Polynomial Kernel calculates high-dimensional relationships?

![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled.png)

 

$(a * b + r)^d$

**a** and **b** refer to two different observations in the dataset

**r** determines the coefficient of the polynomial

**d** sets the degree of the polynomial

$(a * b + 1/2)^2 = ab + a^2b^2 + (1/4)$

$= (a, a^2, (1/2))*(b, b^2, (1/2))$

The Dot Product gives us the high-dimensional coordinates for the data

The first terms are the x-axis coordinates → a, b

The second terms are the y-axis coordinates → $a^2, b^2$

The third terms are the z-axis coordinates → (1/2), (1/2) (we can ignore them)

Thus, we have x and y-axis coordinates for the data in the higher dimension

- x-axis

    ![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled%201.png)

    ![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled%202.png)

- y-axis

    ![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled%203.png)

    ![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled%204.png)

We can ignore the z-axis coordinate since it is a constant value

- In detail (using Dot Products)

    ![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled%205.png)

    it turns out that all we need to do to calculate the high-dimensional relationships is calculate the Dot Products between each pair of points.

    ![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled%206.png)

    ![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled%207.png)

    ![Untitled](day210911%20-%20Support%20Vector%20machines%20Part2%20(Polynom%20f792c5eb7b90440c8e8173796406f0ca/Untitled%208.png)