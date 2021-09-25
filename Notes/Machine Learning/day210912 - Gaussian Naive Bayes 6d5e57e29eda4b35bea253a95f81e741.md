# day210912 - Gaussian Naive Bayes

- What is Gaussian distribution?

    It is also called a "bell shaped curve" because it is a symmetrical curve

    ![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled.png)

    Here are two normal distributions of the height of male humans when born and as adults

    ![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%201.png)

- What is the difference between Probability and Likelihood

    **probability**

    Probabilities are the areas under a fixed distribution

    $pr(data | distribution)$

    ![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%202.png)

    **Likelihood**

    Likelihoods are the y-axis values for fixed data points with distributions that can be moved.

    $L(distribution | data)$

    ![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%203.png)

**Example**

![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%204.png)

![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%205.png)

![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%206.png)

**Graphs with Distributions**

![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%207.png)

Gaussian Naive Bayes is named after the Gaussian distributions that represent the data in the Training Dataset

**When a new one shows up... (adding the new observation)**

→ how are you going to know which class this person should be in?

this one eats 10 grams of popcorn

![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%208.png)

**We should use Naive Bayes**

Let's say 8 of the 16 people in the Training Data Loved Troll2, the initial guess will be 0.5

p(Love Troll 2) = 8/8+8 = 0.5

Likewise... p(No Love Troll 2) = 0.5

**Terminology**

Prior Probabilities: The initial guesses

So to predict whether the new one is in Love Troll 2

get the prior probabilities first → 0.5

times the Likelihood that they eat 10 grams of popcorn → L(popcorn = 20 | Loves)

times the Likelihood that they drink 500 ml of popcorn → L(soda pop = 500 | Loves)

times the Likelihood that they eat 25 grams of candy→ L(candy = 25 | Loves)

0.5 * 0.06 * 0.004 * 0.00000..x

Note: When we get really, really small numbers, it's a good idea to take the log() of everything to prevent something called underflow

![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%209.png)

![Untitled](day210912%20-%20Gaussian%20Naive%20Bayes%206d5e57e29eda4b35bea253a95f81e741/Untitled%2010.png)

It leads up to...

(-0.69) + (-2.8) + (-5.5) + (-155) = -124

log(Loves Troll 2 Score) = -124

Likewise...

log(No Loves troll 2 Score) = -48

And since the score for Does Not Love Troll 2 (-48) is greater than the score for Loves Troll 2 (-124)

We will classify this person as someone who Does Not Love Troll 2

**There is something we should make straight**

Given the first two graphs (for Popcorn, Soda Pop) the new one should have been classified in Love Troll 2 class. But The Likelihood for candy is way too larger than the combined one with Popcorn and Soda pop

We can use Cross Validation to help use decide which things, popcorn, soda pop and/or candy help us make the best Classification