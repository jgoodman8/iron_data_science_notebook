# Gaussian Mixture Model

{% hint style="info" %}
_Sources:_

* \_\_[_Gaussian Mixture Models Explained \(Towards Data Science\)_](https://towardsdatascience.com/gaussian-mixture-models-explained-6986aaf5a95)\_\_
* \_\_[_Gaussian Mixture Models Algorithm Explained \(Cory Maklin\)_](https://towardsdatascience.com/gaussian-mixture-models-d13a5e915c8e)\_\_
{% endhint %}

## What is a Gaussian Mixture?

It is **function composed by several Gaussians**. The **number of Gaussians is equal to the number of clusters** \(_k_\). Each distribution is parametrized by:

* The mean $$\mu$$ which defines its centre.
* The covariance Σ which defines its width.
* The mixing probability $$\pi$$.

The Gaussian density function is given by:

![](../../../../.gitbook/assets/image%20%2881%29.png)

where:

* The sum of every mixing probability must be equal one: $$\sum_{i=1}^K \pi_i = 1$$
* $$D$$is the number of dimensions or features of each instance.
* Each data point $$X$$represents a data point \(a $$1 \times D$$ vector\)
* The mean $$\mu$$ is a $$1 \times D$$ vector.
* And the covariance Σ is a $$D \times D$$ matrix.

## How do we fit the algorithm?

By applying the _Expectation-Maximization algorithm_ widely used for optimization problems where the objective function is that complex.

![](../../../../.gitbook/assets/1-i0wtztoyydvwfpymszpzwq%20%281%29.gif)

## Differences regarding k-Means

* It **accounts for covariance**, which determines the shape of the distribution  This means that meanwhile the **k-means model is that it places a circle** \(or a hyper-sphere\) at the center of each cluster, **a GMM model can handle different shapes**.

![](../../../../.gitbook/assets/image%20%2854%29.png)

* **k-Means performs a hard classification**, but a **GMM model carries out a soft one** by returning the probability that each data point belongs to a certain cluster.

