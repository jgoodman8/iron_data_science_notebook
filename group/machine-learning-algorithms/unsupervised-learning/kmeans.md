# kMeans

{% hint style="info" %}
_Sources:_

* \_\_[_k-Means \(Towards Data Science\)_](https://link.medium.com/5M1Coj4HM0)\_\_
* \_\_[_Step by Step to K-Means Clustering_](https://healthcare.ai/step-step-k-means-clustering/)\_\_
{% endhint %}

## Overview

* It defines a _**k**_ **number of centroids**.
* _k == number of clusters._
* Every instance MUST be assigned to a centroid
* It assignes instances to centroids using the _**inter-cluster sum of squares**._
* Each data point owns to a single cluster.

## The algorithm

1. It **randomly selects** _**k**_ **centroids** from the dataset.
2. It assigns each non-centroid point to a cluster, based on the distances between them \(selects the lower distance\).
3. 
