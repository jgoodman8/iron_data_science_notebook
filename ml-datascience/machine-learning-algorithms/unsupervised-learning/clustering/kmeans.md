# kMeans

{% hint style="info" %}
_Sources:_

* __[_k-Means (Towards Data Science)_](https://link.medium.com/5M1Coj4HM0)__
* __[_Step by Step to K-Means Clustering_](https://healthcare.ai/step-step-k-means-clustering/)__
* __[_KMeans clustering from A to Z_](https://towardsdatascience.com/k-means-clustering-from-a-to-z-f6242a314e9a)__
{% endhint %}

## Overview

* It defines _**k**_** centroids** (_k_ is **manually selected**).
* _k_ $$\Rightarrow$$ _number of clusters._
* Every instance MUST be assigned to a centroid.
* Each data point owns to a single cluster.

## The algorithm

1. **Randomly selects **_**k**_** centroids** from the dataset.
2. **Computes the distances** (euclidean, cosine...) between for each non-centroid point to the _k_ centroids.
3. Assigns each non-centroid point to a cluster, based on the smallest computed distances.
4. Recalculates the cluster centroids: the **new centroid is the average or the mean value of all the cluster instances**.
5. Back to Step 2 until:
   1. &#x20;The maximum number of iterations is reached
   2. The clusters stabilize: when clusters remain the same, centroids remain the same of distances are small enough.

{% hint style="danger" %}
Always converges after enough iterations to a **local optimum**. However, it **doesn't provide a deterministic solution**, due to the random initialization.
{% endhint %}

{% tabs %}
{% tab title="Random initialization" %}
![](<../../../../.gitbook/assets/image (62).png>)
{% endtab %}

{% tab title="Compute centroid distances" %}
![](<../../../../.gitbook/assets/image (66).png>)
{% endtab %}

{% tab title="Assign instances" %}
![](<../../../../.gitbook/assets/image (42).png>)
{% endtab %}

{% tab title="Recalculate centroids" %}
![](<../../../../.gitbook/assets/image (46).png>)
{% endtab %}
{% endtabs %}

## How to choose the optimal _k_?

* Plotting data by picking a different color for each data point gives a good overview.
* Evaluate the [inertia](clustering-metrics.md#inertia) of each cluster. The goal is:
  * &#x20;a low metric value
  * a low number number of clusters
* The [elbow method](https://en.wikipedia.org/wiki/Elbow\_method\_\(clustering\)) is a good tool to select the optimal value of _k_.

![](<../../../../.gitbook/assets/image (67).png>)
