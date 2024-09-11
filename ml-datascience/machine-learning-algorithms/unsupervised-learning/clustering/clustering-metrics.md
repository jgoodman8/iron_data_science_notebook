# Clustering metrics

{% hint style="info" %}
_Sources:_

* [_K-Means Clustering: From A to Z (Towards Data Science)_](https://towardsdatascience.com/k-means-clustering-from-a-to-z-f6242a314e9a)
* [_Clustering performance evaluation (Scikit Learn)_](https://scikit-learn.org/stable/modules/clustering.html#clustering-performance-evaluation)
* [_The Silhouette Loss Function: Metric Learning with a Cluster Validity Index_](https://platform.ai/blog/page/11/the-silhouette-loss-function-metric-learning-with-a-cluster-validity-index/)
* [_ML | Inter-cluster and Intra-cluster distances (Geeks for Geeks)_](https://www.geeksforgeeks.org/ml-intercluster-and-intracluster-distance/)
{% endhint %}

Theses metrics evaluate how good is the clustering structure with no need for external information. Clustering evaluation metrics may belong to one of these types:

* **Intercluster distance**
* **Intracluster distance**
* **Hybrid (combines both)**

## Inertia

* Or **within-cluster sum-of-squares** criterion.
* Tells **how far away the points within a cluster** are.&#x20;
* The range of the score is: $$[0, +\infty )$$. So, the **lowest is better**.

$$
\sum_{i=0}^{n}\min_{\mu_j \in C}(||x_i - \mu_j||^2) \\ \text{where } \mu_j  \text{ is the centroid of each cluster and } x_i \text{ a data point.}
$$

## Silhouette score

* It give information about the inter-cluster distances and the intra-cluster distances.
* Tells **how far away** the instances in one cluster are, **from the instances of another cluster**.&#x20;
* The range of the score is $$[ -1, 1]$$. The **highest is better**.

![](../../../../.gitbook/assets/silhouette\_formula-1.png)





