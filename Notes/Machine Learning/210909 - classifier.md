# Statistics_day210903


reference:
[https://c3.ai/glossary/data-science/classifier/](https://c3.ai/glossary/data-science/classifier/)

From Notion
https://www.notion.so/day210909-classifier-2b8822f70bea4979a81ac8b1dc27ae49

### What is a Classifier?

In data science, a classifier is a type of machine learning algorithm used to assign a class label to a data input. An example is an image recognition classifier to label an image (e.g., “car,” “truck,” or “person”). Classifier algorithms are trained using labeled data; in the image recognition example, for instance, the classifier receives training data that labels images. After sufficient training, the classifier then can receive unlabeled images as inputs and will output classification labels for each image.

Classifier algorithms employ sophisticated mathematical and statistical methods to generate predictions about the likelihood of a data input being classified in a given way. In the image recognition example, the classifier statistically predicts whether an image is likely to be a car, a truck, or a person, or some other classification that the classifier has been trained to identify.

### Why are Classifiers Important?

Classification – i.e., assigning a data input with a specific class label – is a fundamental function of many [enterprise AI](https://c3.ai/what-is-enterprise-ai/) applications, and classifiers are a core element in many of these applications. Classifiers are widely used for a range of common use cases, such as identifying if a customer belongs to a certain segment, identifying whether a financial transaction is fraudulent, or determining whether a piece of field equipment is in operable condition based on a photo or video footage.

Classification is a robust area of ongoing machine learning research and innovation. Significant [academic](https://nlp.stanford.edu/wiki/Software/Classifier#:~:text=The%20Stanford%20Classifier%20is%20a,(weights)%20for%20each%20class.) and commercial effort has been invested in developing a diverse selection of classifier algorithms optimized for different types of classification problems. Numerous robust classifier methods have been developed and many are available through open source libraries, for example [Python classifiers](https://pypi.org/classifiers/) from Pypi.org.

### Classification in Machine Learning

In machine learning and statistics, classification is a supervised learning method in which a computer software learns from data and makes new observations or classifications.

Classification is the process of dividing a set of data into distinct classes. It may be applied to both organized and unstructured data. Predicting the class of data points is the first step in the procedure. Target, label, and categories are common terms for the classes.

Approximating the mapping function from discrete input variables to discrete output variables is the problem of classification predictive modeling. The basic objective is to figure out which category or class the new data belongs in.

There are a couple of different types of classification tasks in machine learning, namely:

- **Binary Classification** – Classification problems with two class labels are referred to as binary classification. In most binary classification problems, one class represents the normal condition and the other represents the aberrant condition.
- **Multi-Class Classification** – Classification jobs with more than two class labels are referred to as multi-class classification. Multi-class classification, unlike binary classification, does not distinguish between normal and pathological results. Instead, examples are assigned to one of a number of pre-defined classes.
- **Multi-Label Classification** – Classification problems with two or more class labels, where one or more class labels may be anticipated for each case, are referred to as multi-label classification. It differs from binary and multi-class classification, which predict a single class label for each case.