# Machine Learning

## What is Machine Learning?

Machine Learning (ML) is a field of computer science that gives computers the ability to learn from data and make decisions or predictions without being explicitly programmed. In traditional programming, rules are hard-coded by developers. In ML, the model learns patterns and relationships from data and uses these to make decisions.

## Types of Machine Learning

1. **Supervised Learning**  
    Supervised learning trains a model using labeled data where each input has a known correct output. The model learns by comparing its predictions with these correct answers and improves over time. It is used for both *classification* and *regression* problems.

2. **Unsupervised Learning**  
    Unsupervised learning works with unlabeled data where no correct answers or categories are provided. The model's job is to find the data, hidden patterns, similarities or groups on its own. This is useful in scenarios where labeling data is difficult or impossible. Common applications are *clustering* and *dimensionality reduction*.

3. **Reinforcement Learning**  
    Reinforcement Learning (RL) trains an agent to make decisions by interacting with an environment. Instead of being told the correct answers, agent learns by trial and error method and gets rewards for good actions and penalties for bad ones.

4. **Semi-Supervised Learning**  
    Semi-supervised learning falls between supervised and unsupervised learning. It uses a small amount of labeled data along with a large amount of unlabeled data.

5. **Self-Supervised Learning**  
    Self-supervised learning (SSL) enables models to train themselves on unlabeled data, instead of requiring massive annotated and/or labeled datasets. 


## Classification and Regression

Supervised machine learning problems often fall into two categories:

**Classification**  
The output is a category or class label.  
Example: Determining whether a tumor is benign or malignant.

**Regression**  
The output is a continuous number.  
Example: Predicting the temperature for tomorrow.

## Overfitting and Underfitting

When training a machine learning model, our goal is not just to make accurate predictions on the training data, but also to ensure that it performs well on unseen data. This is called **generalization**. Machine Learning models are "good" if:
- It learns patterns effectively from the training data.
- It generalizes well to new, unseen data.

Two common problems that prevent generalization are:
1. Overfitting
2. Underfitting

### Overfitting

**Overfitting** happens when a model learns too much from the training data, including details that do not matter (like noise or outliers). As a result, the model works great on training data but fails when tested on new data. 

Overfitting models are like students who memorize answers instead of understanding the topic. They do well in practice tests (training) but struggle in real exams (testing).

### Underfitting

**Underfitting** happens when a model is too simple to capture what is going on in the data. In this case, the model doesn’t work well on either the training or testing data.

Underfitting models are like students who don’t study enough. They do not do well in practice tests or real exams.

## Bias–variance tradeoff

**The bias–variance tradeoff** describes the relationship between a model's complexity, the accuracy of its predictions, and how well it can make predictions on previously unseen data that were not used to train the model. In general, as the number of tunable parameters in a model increases, it becomes more flexible, and can better fit a training data set. That is, the model has lower error or lower **bias**. However, for more flexible models, there will tend to be greater **variance** to the model fit each time we take a set of samples to create a new training data set. It is said that there is greater variance in the model's estimated parameters.

The **bias–variance dilemma** or **bias–variance problem** is the conflict in trying to simultaneously minimize these two sources of error that prevent supervised learning algorithms from generalizing beyond their training set:
    
- The **bias** error is an error from erroneous assumptions in the learning algorithm. High bias can cause an algorithm to miss the relevant relations between features and target outputs (underfitting).
- The **variance** is an error from sensitivity to small fluctuations in the training set. High variance may result from an algorithm modeling the random noise in the training data (overfitting).
