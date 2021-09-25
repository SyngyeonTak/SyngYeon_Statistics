# day210907 - Support Vector Machines 1 / 3

## Maximal Margin Classifier and Support Vector Classifier

- 1 dimensional

    Red dots are not obese mice

    Green dots are obese mice

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled.png)

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%201.png)

    This observation has more mass than the threshold, we classify it as obese

    But that doesn't make sense, because It is much closer to the observations that are not obese

    → This threshold is pretty lame.

    ### How can we get a better threshold??

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%202.png)

    and use the midpoint between them as the threshold

    **Terminology alert**

    Margin : The shortest distance between the observations and the threshold

    Maximal Margin Classifier:  When we use the threshold that gives us the largest margin to make classifications

    Soft margin : When we allow misclassification, the distance between the observations and the threshold is called a Soft Margin

    **How do we know the Soft Margin?**

    The answer is simple: We use Cross-Validation to determine how many misclassification and observations to allow inside of the Soft Margin to get the best classification.

    **Terminology**

    Soft Margin Classifier(Support Vector Classifier): When we use a Soft Margin to determine the location of a threshold

    The name Support Vector Classifier comes from the fact that the observations on the edge and within the Soft Margin are called Support Vectors.

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%203.png)

- 2 dimensional

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%204.png)

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%205.png)

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%206.png)

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%207.png)

    Just like before, we used Cross-Validation to determine that allowing this misclassification results in better classification in the long run

- 3 dimensional

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%208.png)

    To make it look in 3 dimensional, we draw the dot in a different size for the depth.

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%209.png)

    And we classify new observations by determining which side of the plane they are on

    HyperPlane: A hyperplane is a concept in geometry. It is a generalization of the plane into a different number of dimensions. A hyperplane of an n-dimensional space is a flat subset with dimension. By its nature, it separates the space into two half-spaces.

### Support Vector Machines!!!

- Intro

    ![Untitled](day210907%20-%20Support%20Vector%20Machines%201%203%20710e17c364ef4ce9b46778a7a29ecb2b/Untitled%2010.png)