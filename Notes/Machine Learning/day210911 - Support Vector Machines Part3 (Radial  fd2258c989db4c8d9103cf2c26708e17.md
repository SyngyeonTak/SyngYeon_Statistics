# day210911 - Support Vector Machines Part3 (Radial Kernel)

How does the Radial Kernel calculate high-dimensional relationships

![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled.png)

One way to deal with overlapping data is to use a Support Vector Machine with a Radial Kernel

(Radial Basis Function, RBF)

Because the Radial Kernel finds support Vector Classifiers in infinite dimensions, it's not possible to visualize what it does

![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%201.png)

Now let's talk about how the Radial Kernel determines how much influence each observation in the Training dataset has on classifying new observations.

Just like with the Polynomial Kernel, a and b refer to two different Dosage measurements

![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%202.png)

The difference between the measurements is then squared, giving us the squared distance between the two observations.

Thus, the amount of influence one observation has on another is a function of the squared distance

![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%203.png)

(gamma), which is determined by Cross Validation, scales the squared distance, and thus, it scales the influence

For example, if we set gamma = 1 and plug in the Dosages from two observations that are relatively close to each other...

![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%204.png)

![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%205.png)

![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%206.png)

Note: Just like with the polynomial Kernel when we plug values into the Radial Kernel, we get the high-dimensional relationship

![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%207.png)

- **step 1: If r = 0 in Polynomial Kernel**

    Use the Polynomial Kernel to give us intuition into how the Radial Kernel works in Infinite-Dimensions

    When r = 0, the Polynomial Kernel simplifies to a single term...

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%208.png)

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%209.png)

    The new coordinate is just the square of the original measurement on the original axis

    In other words, then r = 0 and d = 2, all the Polynomial Kernel does is shift the data down the original axis

    So setting r= 0 seems silly because no matter what values we use for d, the Dot Products leave the data in the original dimension

- **step 2: If (r = 0 and d = 1) adds (r = 0 and d =2)**

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2010.png)

    This gives us a Dot Product with coordinates for 2-Dimensions.

    The first coordinate is the original Dosage: a, b

    And the second coordinate is $Dosage^2$ : $a^2, b^2$

    Now, what if we just kept adding Polynomial Kernels with r = 0 and increasing d until d = infinity

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2011.png)

    **That would give us a Dot Product with coordinates for an infinite number of dimensions!!!!**

    → That's exactly what the Radial Kernel does, so let's talk about it!

- **step 3: How does the Radial Kernel work? (Radial Kernel Equation)**

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2012.png)

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2013.png)

    Now let's create the Taylor series Expansion of this last term

    - Taylor series Expansion

        ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2014.png)

        Although there are exceptions, the main idea is that a function, f(x)

        ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2015.png)

        What is a?

        The definition of the Taylor Series says that a can be any value as long as f(a) exists...

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2016.png)

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2017.png)

- **step 4: How to use Polynomial Kernel (r = 0) to Radial Kernel**

    Before we move on, let's remember that when we added up a bunch of Polynomial Kernels with r = 0 and d going from 0 to infinity.

    We got a Dot product with coordinates for an infinite number of dimensions

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2018.png)

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2019.png)

    Thus, each term in this Taylor series Expansion contains a Polynomial Kernel with r = 0 and d going from 0 to infinity

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2020.png)

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2021.png)

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2022.png)

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2023.png)

    ![Untitled](day210911%20-%20Support%20Vector%20Machines%20Part3%20(Radial%20%20fd2258c989db4c8d9103cf2c26708e17/Untitled%2024.png)

    And, at long last, we see that the Radial Kernel is equal to a Dot Product that has coordinates for an infinite number of dimensions

    That means that when we plug numbers into the Radial Kernel and do the math...

    The value we get at the end is the relationship between the two points in infinite dimensions.