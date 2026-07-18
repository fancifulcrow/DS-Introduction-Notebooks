# Decision Trees

## Introduction

A decision tree is a supervised learning algorithm, which is utilized for both classification and regression tasks. It has a hierarchical, tree structure, which consists of a root node, branches, decision nodes and leaf nodes. It works like a flowchart help to make decisions step by step.

- **Root Node:** The first node, representing the entire dataset, which gets split into two or more homogeneous sets.
- **Decision Nodes:** Nodes where the data is split further.
- **Leaf/Terminal Nodes:** Nodes that represent the final decision or output (e.g., class labels or predicted values).
- **Branches:** Represent the outcome of a decision and connect nodes.

<p align="center">
<img src="./images/Decision_Tree.jpg" alt="Decision Tree of the survival of passengers on the Titanic Source:Wikimedia Commons" width="480">
</p>

## Splitting Criteria

One of the most important tasks when building a decision tree is choosing the best attribute to split the data at each node. This decision significantly affects the accuracy, efficiency, and interpretability of the final tree. To do this, decision tree algorithms use **splitting criteria**, which measure how well a particular feature separates the data into more homogeneous subsets.

The most commonly used splitting criteria are:

- **Information Gain** (classification)
- **Gini Index** (classification)
- **Mean Squared Error (MSE)** (regression)

### Entropy and Information Gain

It is difficult to explain information gain without first discussing entropy.

**Entropy** is a metric to measure the impurity in a given attribute. It specifies randomness in data. Entropy comes from information theory. The higher the entropy, the more the information content.

$$
\text{Entropy}(S) = -\sum_{c \in C} p(c) \log_2 p(c)
$$

where:
* $S$ represents the data set that entropy is calculated on
* $c$ represents the classes in set $S$
* $p(c)$ represents the proportion of data points that belong to class $c$ out of the total data points in set $S$

Entropy is always $\geq 0$. For a binary classification problem it is bounded between 0 and 1. Entropy equals zero when all samples belong to a single class (a pure node), and reaches its maximum when samples are spread equally across all classes. To find the best feature to split on, we prefer the attribute that leads to the smallest weighted entropy in the child nodes.

**Information gain** represents the difference in entropy before and after a split on a given attribute. It tells us how important a given attribute of the feature vectors is. The attribute with the highest information gain will produce the best split.

$$
\text{Information Gain}(S, \alpha) = \text{Entropy}(S) - \sum_{v \in \text{values}(\alpha)} \frac{|S_v|}{|S|} \text{Entropy}(S_v)
$$

where:
* $\alpha$ represents a specific attribute
* $\text{Entropy}(S)$ is the entropy of dataset $S$
* $\frac{|S_v|}{|S|}$ represents the proportion of the values in $S_v$ to the number of values in dataset $S$

In other words:
$$
\text{Information Gain} = \text{Entropy of Parent Node} - \text{Weighted Average Entropy of Child Nodes}
$$

### Gini Index

**Gini index** is the probability of incorrectly classifying a randomly chosen data point from the dataset if it were labeled according to the class distribution of the dataset. It measures how often a randomly chosen element would be misclassified based on the label distribution in a node.

Similar to entropy, if the set $s$ is pure (i.e., all instances belong to one class), the impurity is zero.

$$
\text{Gini Index}(S) = 1 - \sum_{c \in C} p(c)^2
$$

- **Gini = 0** when all samples are in a single class (pure).
- **Higher Gini** values indicate more class mixing (impurity).
- Gini is computationally faster.

### Mean Squared Error

When a decision tree is used for **regression** (predicting continuous values), impurity measures like Gini index and entropy are not appropriate because there are no class labels. Instead, the most common splitting criterion is **Mean Squared Error (MSE)**.

The idea is to choose the split that produces child nodes whose target values are as close together as possible. MSE at a node measures the average squared deviation of each sample's target value from the node's mean prediction:

$$
\text{MSE}(S) = \frac{1}{|S|} \sum_{i \in S} (y_i - \bar{y})^2
$$

where:
* $S$ is the set of samples at the node
* $y_i$ is the target value of sample $i$
* $\bar{y}$ is the mean target value of all samples in $S$

At each step, the algorithm selects the split that produces the greatest MSE reduction:

$$
\text{MSE Reduction} = \text{MSE}(S) - \sum_{v} \frac{|S_v|}{|S|} \text{MSE}(S_v)
$$

At each leaf node, the prediction is simply the mean of the target values of the training samples that reach that node.

- **MSE = 0** at a leaf means all samples have the same target value (a perfect split).
- **Higher MSE reduction** indicates a more informative split.

While MSE is the standard and most widely used criterion for regression trees, alternatives exist for specific use cases such as **Mean Absolute Error (MAE)** for greater robustness to outliers, and **Poisson deviance** when the target represents count data.

## Ensemble Methods

**Ensembling** is a technique where multiple models are combined to improve performance, reduce errors, and increase robustness. Instead of relying on a single model, ensembling leverages the strengths of multiple models to produce a better final prediction.

For Decision Trees, there are two basic ensembling techniques:
- Bagging
- Boosting

### Bagging (Bootstrap Aggregating)

Bagging is an ensemble method that reduces variance and improves stability by training multiple models independently on different random subsets of the data.
- Multiple models are trained independently in parallel on different random subsets of the data.
- The final prediction is made by majority voting (classification) or averaging (regression).

Example: Random Forest

### Boosting

Boosting is an ensemble method that reduces bias by training models sequentially, where each new model focuses on correcting the errors of the previous ones.
- Models are trained sequentially, where each model corrects the errors of the previous one.
- The final prediction is a weighted combination of all models.

Examples: XGBoost, LightGBM, Catboost
