# day210912 - Naive Bayes

The probabilities of discrete, individual words, and **not** the probability of something **continuous**, like weight or height, these Probabilities are also called **Likelihoods**.

- **The issue 1**

    ![Untitled](day210912%20-%20Naive%20Bayes%20e81e3cd8354e4462bd1e5e372b5b1dd0/Untitled.png)

    Let's say we want to separate normal messages and spam messages.

    We can sort that out by words. But what if some words are used for both kinds messages?

    - **Normal Message**

        For example, since 8 of the 12 messages are normal messages, our initial guess will be 0.67

        (8 from normal messages, the rest 4 from spam)

        p(N) The initial guess that we observe Normal messages is called a Prior Probability

        Now we multiply that initial guess by the probability that the word Dear occurs in a normal message

        And the probability that the word Friend occurs in a normal message.

        **p(N) * p(Dear | N) * p(Friend | N) = 0.09**

        We can think of 0.09 as the score that Dear Friend gets if it is a Normal Message

        However, technically, it is proportional to the probability that the message is normal, given that it says Dear Friend.

        **p(N | Dear Friend) (is proportional to) 0.09**

    - **Spam**

        Since 4 of the 12 messages are spam, our initial guess will be 0.33

        ![Untitled](day210912%20-%20Naive%20Bayes%20e81e3cd8354e4462bd1e5e372b5b1dd0/Untitled%201.png)

         

        Now we multiply that initial guess by the probability that the word Dear occurs in a normal message

        And the probability that the word Friend occurs in a normal message.

        **p(S) * p(Dear | S) * p(Friend | S) = 0.01**

        We can think of 0.01 as the score that Dear Friend gets if it is a spam

        However, technically, it is proportional to the probability that the message is normal, given that it says Dear Friend.

        **p(S | Dear Friend) (is proportional to) 0.01**

    **p(N | Dear Friend) (is proportional to) 0.09**

    **p(S | Dear Friend) (is proportional to) 0.01**

    Since the score we got for Normal message, 0.09 is greater than the score we got for Spam, 0.01

    **We will decide that Dear Friend is a Normal Message**

- **The issue 2**

    How to classify the word **Lunch Money Money Money Money** 

    Calculate the score like what we did before...

    p(N) *  p(Lunch | N) * p(Money | N) * p(Money | N) * p(Money | N) * p(Money | N) = 0.000002

    p(S) *  p(Lunch | S) * p(Money | S) * p(Money | S) * p(Money | S) * p(Money | S)  = 0

    Why zero? → p(Lunch | S) is zero...

    **This is a problem**

    ![Untitled](day210912%20-%20Naive%20Bayes%20e81e3cd8354e4462bd1e5e372b5b1dd0/Untitled%202.png)

    To work around this problem, people usually add 1 count, represented by a black box, to each word in the histograms

    Note: The number of counts we add to each word is typically referred to with the Greek letter alpha

    In this case, alpha = 1, but we could have set it to anything

    Anyway, now when we calculate the probabilities of observing each word we never get 0.

    For example, the probability of seeing Lunch, given that it is in spam.

    p(Lunch | Spam) = $1/(7+4) = 0.09$

    Note: Adding counts to each word does not change our initial guess that a message is normal or spam

    why? → Because adding a count to each word did not change the number of messages in the Training Dataset that are normal(8) or spam(4)

    We add counts for each word, somehow we get a greater score for spam.

    We classify the message as spam

    ![Untitled](day210912%20-%20Naive%20Bayes%20e81e3cd8354e4462bd1e5e372b5b1dd0/Untitled%203.png)

- **Why Naive Bayes is naive?**

    The thing that makes Naive Bayes so naive is that it treats all word orders the same

    For example, the Normal message score for the phrase, Dear Friend is the exact same as the score for Friend Dear

    Every language has grammar rules and common phrases, but Naive Bayes ignores all of that stuff....