# Chapter 1 - Exercises

### 1. How would you define machine learning?

Machine learning is the science of using a computer to solve a problem without explicitly programming it, but instead
allowing it to learn from data.

### 2. Can you name four types of applications where it shines?

* Complex problems with no normal algorithmic solution
* Problems where the solution requires many rules and edge-cases
* Problem domains that are dynamic and frequently-changing
* Data-mining: finding patterns in data that can be used by humans

### 3. What is a labelled training set?

A dataset that contains both features and the target value to be predicted (e.g. a class label in classification or a
target value in regression).

### 4. What are the two most common supervised tasks?

Regression and classification.

### 5. Can you name four common unsupervised tasks?

Anomaly detection, clustering, dimensionality reduction, visualisation algorithms.

### 6. What type of algorithm would you use to allow a robot to walk in various unknown terrains?

Reinforcement learning.

### 7. What type of algorithm would you use to segment your customers into multiple groups?

Clustering. _(or classification if you already know what the groups are)_

### 8. Would you frame the problem of spam detection as a supervised learning problem or an unsupervised learning problem?

It's a supervised learning problem - the computer can't inherently learn what spam is without outside guidance.

### 9. What is an online learning system?

An online learning system learns from new examples as they arrive in a live setting (as opposed to offline/batch
learning which only learns at training time).

### 10. What is out-of-core learning?

This is where an algorithm is trained on a dataset that can't fit into main memory, meaning it needs to run training
steps over batches of the whole dataset.

### 11. What type of algorithm relies on a similarity measure to make predictions?

An instance-based learning algorithm.

### 12. What is the difference between a model parameter and a model hyperparameter?

A model parameter is a value in the model that gets updated with each training step and has some effect on the
predictions. A hyperparameter describes an aspect of the model or the training process itself, and is tuned separately.

### 13. What do model-based algorithms search for? What is the most common strategy they use to succeed? How do they make predictions?

Model-based algorithms search for parameters to a model that they can use to predict a target value for unseen data
instances. They're trained by minimsiing a cost function. They make predictions by running inference using the trained
values for the parameters.

### 14. Can you name four of the main challenges in machine learning?

Not enough data; poor-quality data; overfitting; data drift.

### 15. If your model performs great on the training data but generalizes poorly to new instances, what is happening? Can you name three possible solutions?

This would mean that the model has been overfit. The solutions could be to increase regularization (i.e. reduce the
degrees of freedom of the model); use a simpler model (because a complex model might be able to learn the whole training
set); or get more data on which to train.

### 16. What is a test set, and why would you want to use it?

This is a portion of the dataset that is not trained on and is used to evaluate the model (by estimating the
generaliaztion error). It's important to use this to understand how your model might generalize to unseen data in a live
setting.

### 17. What is the purpose of a validation set?

This is a subset of the training set which is held out during training and used for validation during the training
process - i.e. it's a test set that you can use more than once. It's used to help decide on a final model architecture
to train - at which point it gets folded back into the training set.

### 18. What is the train-dev set, when do you need it, and how do you use it?

This is a further subset of the training set. You might need this when you're not sure how similar your dataset is to
real-world conditions. You train on your training set and evaluate on your train-dev set (similar to how you use a
validation set). When you're happy that you're not overfitting, you then run your model on the validation set. If you
perform poorly here, then your training data isn't representative of the evaluation data.

### 19. What can go wrong if you tune hyperparameters using the test set?

You'll overfit and your model won't generalize well to new data.
