# day211112 - KnearsNeighbor Algorithm

[https://www.hindawi.com/journals/wcmc/2021/5520990/](https://www.hindawi.com/journals/wcmc/2021/5520990/)

### Abstract

nearest neighbor (NN) is a simple and widely used classifier; it can achieve comparable performance with more complex classifiers including decision tree and artificial neural network. Therefore, NN has been listed as one of the top 10 algorithms in machine learning and data mining. On the other hand, in many classification problems, such as medical diagnosis and intrusion detection, the collected training sets are usually class imbalanced. In class imbalanced data, although positive examples are heavily outnumbered by negative ones, positive examples usually carry more meaningful information and are more important than negative examples. Similar to other classical classifiers, NN is also proposed under the assumption that the training set has approximately balanced class distribution, leading to its unsatisfactory performance on imbalanced data. In addition, under a class imbalanced scenario, the global resampling strategies that are suitable to decision tree and artificial neural network often do not work well for NN, which is a local information-oriented classifier. To solve this problem, researchers have conducted many works for NN over the past decade. This paper presents a comprehensive survey of these works according to their different perspectives and analyzes and compares their characteristics. At last, several future directions are pointed out.

### 1. Introduction

nearest neighbor (NN) [1] has simple implementation and supreme performance and can achieve comparable performance with more sophisticated classifiers including decision tree [2], artificial neural network [3], and support vector machine [4]. Therefore, NN has been listed as one of the top 10 algorithms in data mining and machine learning [5, 6]. NN has been utilized in many applications, such as pattern recognition [7], feature selection [8], and outlier detection [9]. For a test example with unknown class label, NN makes a decision by employing the local information surrounding the test example. Concretely, NN first simply stores all the training examples; then, in the classification phase, it takes the class occurring most frequently in the () nearest training examples of the test example as the classification result. That is, NN makes a decision according to the class distribution characteristics in the  neighborhood of a test example.

Nowadays, machine learning and data mining techniques are widely used in many aspects of the information society. However, for some applications such as medical diagnosis [10], system intrusion detection [11], and network fraud detection [12], the collected training example set is usually class imbalanced, i.e., there is a large difference among the sizes of different classes. For instance, in medical diagnosis data, the majority examples are descriptions of normal patients (negative examples), and only a small proportion of examples are representatives of special patients suffering a rare disease (positive examples). But if a special patient is erroneously classified as a normal patient, the best treatment time will be missed and serious consequences will be caused. For computer network intrusion detection data, the majority examples denote the normal access data (negative examples) and only the minority examples denote the illegal access data (positive examples). Similarly, misclassifying illegal access as a legal one will lead to the disclosure of a unit’s inner data or the steal of bank account information. From the above two instances, it can be seen that, in class imbalanced data, although the positive class is heavily outnumbered by the negative class, the positive class is usually the one in which we are more interested and is more important than the negative class. The positive class is also named the minority class while the negative class is also called the majority class.

Similar to classical classifiers such as decision tree, artificial neural network, and support vector machine, NN is also proposed based on the assumption that a training set has approximately balanced class distribution, i.e., the classes have roughly the same number of training examples. In addition, these algorithms all employ the overall classification accuracy as the optimization objective in the classifier training phase, leading to their unsatisfactory performance on class imbalanced data. For NN, it takes the majority class in the  neighborhood of a test example as the classification result; this majority voting-based classification rule further degrades its performance on a class imbalanced problem. This is because the positive examples are usually sparse in the  neighborhood of a test example [6], i.e., most examples in the  neighborhood are usually negative examples; thus, the positive examples are often misclassified as negative ones by NN, leading to the poor classification performance for positive examples. For instance, in the binary classification problem shown in Figure [1](https://www.hindawi.com/journals/wcmc/2021/5520990/fig1/) (circles denote negative examples, triangles denote positive examples, and the cross denotes a test example), when  equals 7, there are 4 negative examples (N1-N4) and 3 positive examples (P1-P3) in the  neighborhood; obviously, NN classifies the test example as the negative class although it actually belongs to the positive class.

[https://static-01.hindawi.com/articles/wcmc/volume-2021/5520990/figures/5520990.fig.001.svgz](https://static-01.hindawi.com/articles/wcmc/volume-2021/5520990/figures/5520990.fig.001.svgz)

**Figure 1**[](https://www.hindawi.com/journals/wcmc/2021/5520990/fig1/)

Classical NN performs poorly on positive examples (cited from Reference [12]).

Experiments conducted in Reference [13] indicate that SMOTE oversampling integrated with Random Undersampling (RUS) [14] or SMOTE oversampling integrated with the cost-sensitive MataCost method [15] can both significantly improve the performance of C4.5 decision tree [2] on class imbalanced data. Unfortunately, these strategies do not work well for improving NN in a class imbalanced scenario. The authors in [13] give the explanation from the following aspect: NN makes a decision by investigating the *local* neighborhood of a test example, while the resampling and cost-sensitive strategies are *global* methods and are naturally inappropriate to NN. Therefore, special methods for NN need to be designed under the class imbalanced scenario.

As can be seen from the above illustration, improving NN performance on imbalanced data is an important topic, which is of great significance to the expansion of its application fields and the enhancement of its practical utility. Over the past decade, researchers have conducted many works and proposed many methods. This paper tries to give a comprehensive survey of these works according to their perspectives and analyzes and compares their characteristics, which serves as a foundation for further study in this field.

The rest of this paper is organized as follows. The weighting strategy-based methods are illustrated in Section [2](https://www.hindawi.com/journals/wcmc/2021/5520990/#methods-based-on-weighting-strategy), the local geometrical structure-based methods are illustrated in Section [3](https://www.hindawi.com/journals/wcmc/2021/5520990/#methods-based-on-local-geometric-structure-of-data), Section [4](https://www.hindawi.com/journals/wcmc/2021/5520990/#fuzzy-logic-based-methods) introduces the fuzzy logic-based methods and followed by a category of methods based on missing positive example estimation in Section [5](https://www.hindawi.com/journals/wcmc/2021/5520990/#methods-based-on-missing-positive-data-estimation), Section [6](https://www.hindawi.com/journals/wcmc/2021/5520990/#novel-distance-metric-based-methods) presents methods based on novel distance metrics while Section [7](https://www.hindawi.com/journals/wcmc/2021/5520990/#methods-based-on-dynamic-sized-neighborhoods) presents dynamic-sized neighborhood-based methods, and conclusions and future work are presented in Section [8](https://www.hindawi.com/journals/wcmc/2021/5520990/#conclusion).