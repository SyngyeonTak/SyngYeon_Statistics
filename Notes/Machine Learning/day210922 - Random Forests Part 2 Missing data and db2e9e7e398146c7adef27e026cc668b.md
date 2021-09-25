# day210922 - Random Forests Part 2
Missing data and sample Clustering

### **Random Forests consider 2 types of missing data**

1) Missing data in the original dataset used to create the random forest

→ The general idea for dealing with missing data in this context is to make an initial guess that could be bad, then gradually refine the guess until it is (hopefully) a good guess.

- The initial (possibly bad) guess for the blocked arteries value is just the most common value for "Blocked Arteries". "No" occurs in 2 out of 3 samples. → no is our initial guess
- Now we want to refine these guesses. We do this by first determining which samples are similar to the one with missing data.
    - **How to determine the similarity**

        Step 1) Build a random forest.

        Step 2) Run all of the data down all of the trees.

        Step 3) Figure out which samples run through the same path for the result.

        → this is how we get the similarity

        → We can use the proximity matrix

        ![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled.png)

        Step 4) We do the exact same thing for the next tree

        ![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%201.png)

    - **The results in the matrix**

        We divide each proximity value by the total number of trees. In this example, assume we had 10 trees

        ![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%202.png)

        Now we use the proximity values for sample 4 to make better guesses about the missing data.

    - **How to get the final proximity for possible values**

        ![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%203.png)

        The proximity value for Sample 2 → $\frac{0.1}{0.1+0.1+0.8}$

        ![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%204.png)

        The weight for Yes is 0.1

        The weighted frequency for "Yes" is 0.03

        We do the same thing for the weighted frequency for "No"

        → the one for "No" is 0.6

![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%205.png)

2) Missing data in a new sample that you want to categorize

- We hypothetically put Yes and No. And, see which value is the most likely for the missing data.
- And we run each case down all of the trees
- And conclude the case that is labeled more is the final value for the missing data

![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%206.png)

- **Other things we can know from the proximity matrix**

    ![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%207.png)

    With distance matrix, we can even many kinds of maps

    ![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%208.png)

    ![Untitled](day210922%20-%20Random%20Forests%20Part%202%20Missing%20data%20and%20db2e9e7e398146c7adef27e026cc668b/Untitled%209.png)