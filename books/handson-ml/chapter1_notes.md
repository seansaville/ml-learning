# Chapter 1: The Machine Learning Landscape

## What is machine learning?

Machine learning is programming computers to learn from data. By "learn", we mean that the computer measurably improves
a performance metric for a task as it continues to experience that task.

We use machine learning for problems that are too complex to be solved by traditional algorithms. These problems might:

* Require huge lists of rules and special handling for many edge-cases
* Be dynamic, requiring regular changes to the algorithm in order to maintain performance
* Be too complex for traditional algorithms

Machine learning is also useful for data-mining: using a learning algorithm to discover patterns in a dataset.

## Types of machine learning systems

Machine learning systems can be categorised in a number of ways based on how they are trained and how they work.

### Supervision

**Supervised learning:** Training an algorithm on labelled data. Examples of this are classification and
regression.

**Unsupervised learning:** Training an algorithm on unlabelled data. Examples of this are clustering, dimensionality
reduction, and anomaly detection.

**Semi-supervised learning:** Generating a fully labelled dataset from a fully unlabelled one, then using a supervised
learning algorithm on the resulting dataset. An example of this is image reconstruction - take a dataset of images,
randomly mask them to produce a labelled training set of masked images and their reconstruction, then train an algorithm
to recover the full image.

**Reinforcement learning:** Agents learn a task by observing their environment, choosing actions, and receiving rewards
or penalities.

### Batch vs. online learning

**Batch learning:** This is where systems do not learn incrementally - they are trained on a dataset and then deployed
to production, from which point they will no longer be updated. This can lead to model rot/data drift over time; the
solution is typically to retrain the model at a suitable frequency (taking into account the cost of retraining).

**Online learning:** This is where systems learn incrementally, either from one data instance at a time or in
mini-batches. Each learning step is cheap and runs quickly, so the system can quickly react to changing data. How
quickly they react is controlled by the learning rate - a high learning rate means the system forgets history faster.
Data quality monitoring is extremely important here, because your models learn from bad data rather than just perfoming
badly on it.

### Instance-based vs. model-based learning

The question here is "how do machine learning systems generalize beyond their training data?"

**Instance-based-learning:** The system learns examples from the training set by heart, and then generalizes by
comparing new instances to the training set using a measure of similarity. An example of this is k-nearest neighbors.

**Model-based learning:** The system builds a model of the examples during training, then uses this model to make
predictions.


## Main challenges of machine learning

**Not enough training data:** It takes a lot of data to get machine learning algorithms to actually work. In fact,
[this paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/acl2001.pdf) claims that data quantity
can make model choice irrelevant.

**Non-representative training data:** Your system can't generalize if the training data isn't representative of the
test data. Keep sampling bias in mind.

**Poor-quality data:** If your data has many outliers or is full of noise, the learning problem gets much harder.
Cleaning data is not exciting but is crucial!

**Irrelevant features:** Garbage in, garbage out. Feature selection and extraction are key here.

**Overfitting:** If your model is too complex for the amount or quality of training data, you'll overfit as the model
is essentially just memorising the entire training set. Regularization can help here: constrain the model in order to
reduce the likelihood of overfitting. Hyperparameters can be used to control this and tuned during the research process.

**Underfitting:** If your model is too simple for the training data, it won't be able to learn the structure and will
make poor predictions.


## Testing and validating

It's important to know how well your model is actually generalizing to new data. Typically we do this by splitting the
dataset up into a training set and a test set. We can estimate the generalization error by training on the training set
only and evaluating on the test set.

But, be careful - in this scenario, the test set can only be used once - otherwise you'll overfit to your test data and
reduce the ability of your model to generalize. The test set is a proxy for the real world, and using it multiple times
breaks that.

The train-test split is a bit more nuanced in reality. For example, if you wanted to try different model architectures
to see how they generalise, you could create a _validation set_ by further sub-dividing your _training set_. You then
train your candidate models on the _training set_, evaluate them on the _validation set_, and choose the best one. This
is then evaluated on the _test set_ to get an estimate of the true generalization error. Cross-validation takes this
approach further by creating many small validation sets and averaging out their error.

The training set, validation set, and test set all need to be equally representative of the real-world conditions into
which the model is going to be deployed. There are scientific approaches for ensuring this, e.g. the _train-dev_ set.
