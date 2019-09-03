# Supervised vs Unsupervised learning

{% hint style="info" %}
 _More reading:_ [_What is the difference between supervised and unsupervised machine learning? \(Quora\)_](https://www.quora.com/What-is-the-difference-between-supervised-and-unsupervised-learning-algorithms)
{% endhint %}

### Supervised learning

* It requires **labeled data** for training. 
* Tasks are mainly focused on **getting a** _**solution**_ **or** _**prediction**_ expressed as a:
  * Classification
  * Regression

### Unsupervised learning

* It does **not require labeled data** due to it does not perform training.
* Tasks are mainly focused on **getting** _**insights**_ **or** _**guesses**_ through:
  * Clustering
  * Visualization
  * Dimensionality reduction
  * Asociation mining

## KNN vs kMeans

{% hint style="info" %}
 _More reading:_

* [_How is the k-nearest neighbor algorithm different from k-means clustering? \(Quora\)_](https://www.quora.com/How-is-the-k-nearest-neighbor-algorithm-different-from-k-means-clustering)
* \_\_[_KNN \(Towards Data Science\)_](https://towardsdatascience.com/knn-k-nearest-neighbors-1-a4707b24bd1d)\_\_
* \_\_[_k-Means \(Towards Data Science\)_](https://towardsdatascience.com/understanding-k-means-clustering-in-machine-learning-6a6e67336aa1)\_\_
{% endhint %}

### K-Nearest Neighbors

* Supervised algorithm
* Based in **how similar is an instance from its k neighbors**
* There is no training
* It measures the distance between instances \(Euclidian, Manhattan...\)

#### **How it works**

![](../../.gitbook/assets/image%20%288%29.png)

For every unlabeled instance \(the ones to be classified\):

1. It measures the distance to every labeled sample.
2. It sorts the distances \(asc\) 
3. It selects the first k instances
4. It takes the class that appears the most times on the selected k instances.

### kMeans

* Unsupervised algorithm
* Clustering algorithm
* Iterativelly assigns data to k groups



