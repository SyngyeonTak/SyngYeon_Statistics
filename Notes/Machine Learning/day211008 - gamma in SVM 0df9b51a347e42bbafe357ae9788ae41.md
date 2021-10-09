# day211008 - gamma in SVM

[https://scikit-learn.org/stable/auto_examples/svm/plot_rbf_parameters.html](https://scikit-learn.org/stable/auto_examples/svm/plot_rbf_parameters.html)

This example illustrates the effect of the parameters `gamma` and `C` of the Radial Basis Function (RBF) kernel SVM.

Intuitively, the `gamma` parameter defines how far the influence of a single training example reaches, with low values meaning ‘far’ and high values meaning ‘close’. The `gamma` parameters can be seen as the inverse of the radius of influence of samples selected by the model as support vectors.

The `C` parameter trades off correct classification of training examples against maximization of the decision function’s margin. For larger values of `C`, a smaller margin will be accepted if the decision function is better at classifying all training points correctly. A lower `C` will encourage a larger margin, therefore a simpler decision function, at the cost of training accuracy. In other words `C` behaves as a regularization parameter in the SVM.

![Untitled](day211008%20-%20gamma%20in%20SVM%200df9b51a347e42bbafe357ae9788ae41/Untitled.png)

The behavior of the model is very sensitive to the `gamma` parameter. If `gamma` is too large, the radius of the area of influence of the support vectors only includes the support vector itself and no amount of regularization with `C` will be able to prevent overfitting.

When `gamma` is very small, the model is too constrained and cannot capture the complexity or “shape” of the data. The region of influence of any selected support vector would include the whole training set. The resulting model will behave similarly to a linear model with a set of hyperplanes that separate the centers of high density of any pair of two classes.

For intermediate values, we can see on the second plot that good models can be found on a diagonal of `C` and `gamma`. Smooth models (lower `gamma` values) can be made more complex by increasing the importance of classifying each point correctly (larger `C` values) hence the diagonal of good performing models.

Finally, one can also observe that for some intermediate values of `gamma` we get equally performing models when `C` becomes very large. This suggests that the set of support vectors does not change anymore. The radius of the RBF kernel alone acts as a good structural regularizer. Increasing `C` further doesn’t help, likely because there are no more training points in violation (inside the margin or wrongly classified), or at least no better solution can be found. Scores being equal, it may make sense to use the smaller `C` values, since very high `C` values typically increase fitting time.

On the other hand, lower `C` values generally lead to more support vectors, which may increase prediction time. Therefore, lowering the value of `C` involves a trade-off between fitting time and prediction time.

We should also note that small differences in scores results from the random splits of the cross-validation procedure. Those spurious variations can be smoothed out by increasing the number of CV iterations `n_splits` at the expense of compute time. Increasing the value number of `C_range` and `gamma_range` steps will increase the resolution of the hyper-parameter heat map.

**The things to make straight**

**gamma**: defines how far the influence of a single training example reaches

low values - far

high values - close

**What does it actually mean??**

Let's picture a decision line. If I have a low value of gamma, it takes the far observations into consideration. If it is a high value, it is the other way around.

**Why does it even matter?**

If it is high values of gamma, it ends up with a fairly wiggly decision boundary. It could cause overfitting. Only the nearest values will influence the boundary.

![Untitled](day211008%20-%20gamma%20in%20SVM%200df9b51a347e42bbafe357ae9788ae41/Untitled%201.png)

High gamma

![Untitled](day211008%20-%20gamma%20in%20SVM%200df9b51a347e42bbafe357ae9788ae41/Untitled%202.png)

Low gamma

**In other words**

Low values indicate a large similarity radius which results in more points being grouped together

For high values, the points need to be very close to each other in order to be considered in the same group.