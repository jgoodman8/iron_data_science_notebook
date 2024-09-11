# PCA

{% hint style="info" %}
_Credits:_

* [_Understanding Principal Components Analysis (Rishav Kumar)_](https://medium.com/@aptrishu/understanding-principle-component-analysis-e32be0253ef0)
* [_Understanding Principal Components Analysis (Chathurangi Shyalika  )_](https://medium.com/datadriveninvestor/principal-components-analysis-pca-71cc9d43d9fb)
* [_StatQuest: Principal Component Analysis, Step-by-Step  &#x20;(YouTube)_](https://www.youtube.com/watch?v=FgakZw6K1QQ)
{% endhint %}

## Overview

In real-world data analysis tasks we analyze complex data. At first, more features increase performance. However, at some point as the dimensions of data increases, the difficulty to visualize it and perform computations on it also increases. This is called **the course of dimensionality**.&#x20;

Principal Components Analysis solves this problem by making a **dimensionality reduction**. It performs these tasks by what is called in data science _**feature extraction**._

If any good data scientist could choose an **ideal dataset**, it would be plenty of **features with a high degree of independence** from each other. Unfortunately, real-world datasets are not alike.

### Related concepts

{% hint style="success" %}
Check out the  [**Variance**](../../statistics/the-basics.md#variance) and [**Covariance**](../../statistics/the-basics.md#covariance) concepts!
{% endhint %}

#### Eigenvectors

It is a **vector** whose **direction remains unchanged** when a linear transformation is applied to it.

#### Eigenvalues

It is a scalar which corresponds and represents each eigenvector. The corresponding eigenvalue is a number that **indicates how much variance there is in the data along that eigenvector** (or principal component).

## How does it work?

> PCA finds a new **set of dimensions** (or a set of basis of views) such that all the dimensions are **orthogonal** (and hence linearly independent) and **ranked according to the variance of data** along them. It means more important principle axis occurs first. (more important = more variance/more spread out data)

The steps:

1. Calculate covariance matrix _X_ of data points.
2. Calculate [eigen vectors](https://en.wikipedia.org/wiki/Eigenvalues\_and\_eigenvectors) and corresponding eigen values. \[[Panic button](http://setosa.io/ev/eigenvectors-and-eigenvalues/)]
3. Choose first k eigen vectors and that will be the new k dimensions.
4. Transform the original n dimensional data points into k dimensions.

> The principle components are the eigenvectors of the covariance matrix of the original dataset. They correspond to the direction (in the original n-dimensional space) with the **greatest variance in the data**.

{% hint style="warning" %}
In construction...
{% endhint %}
