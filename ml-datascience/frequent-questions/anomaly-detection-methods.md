# Anomaly detection methods

{% hint style="info" %}
_Sources & credit:_

* __[_What machine learning technique is usually used to solve anomaly detection? (Quora)_](https://www.quora.com/What-machine-learning-technique-is-usually-used-to-solve-anomaly-detection)__
* __[_How to use machine learning for anomaly detection and condition monitoring (Vegard Flovik)_](https://towardsdatascience.com/how-to-use-machine-learning-for-anomaly-detection-and-condition-monitoring-6742f82900d7)__
* __[_5 Ways to Detect Outliers/Anomalies That Every Data Scientist Should Know (Will Badr)_](https://towardsdatascience.com/5-ways-to-detect-outliers-that-every-data-scientist-should-know-python-code-70a54335a623)__
* __[_A Brief Overview of Outlier Detection Techniques (Sergio Santoyo)_](https://towardsdatascience.com/a-brief-overview-of-outlier-detection-techniques-1e0b2c19e561)__
* __[_Intuitively Understanding Variational Autoencoders (Irhum Shafkat)_](https://towardsdatascience.com/intuitively-understanding-variational-autoencoders-1bfe67eb5daf)__
* __[_DBSCAN: What is it? When to use it? How to use it?_](https://medium.com/@elutins/dbscan-what-is-it-when-to-use-it-how-to-use-it-8bd506293818)
* __[_Best clustering algorithms for anomaly detection_](https://towardsdatascience.com/best-clustering-algorithms-for-anomaly-detection-d5b7412537c8)__
{% endhint %}

Depending on the **presence or lack of labels**, there are two approaches to face yourself to an anomaly detection problem.

## As an unbalanced classification problem

When we are given a set of observations with labels that indicate whether each point is an anomaly or not, this can be seen as a **binary classification problem**. So we can use any classifier we like. The only issue here is that **anomalies are by definition rare events**, so you’ll have to deal with class imbalance.

{% content-ref url="how-to-deal-with-imbalanced-datasets.md" %}
[how-to-deal-with-imbalanced-datasets.md](how-to-deal-with-imbalanced-datasets.md)
{% endcontent-ref %}

## As an unsupervised problem

In this scenario, we are given a **set of points without class labels**. Some of them are anomalies and some aren’t, but you don’t know which is which. The goal here is to operationalize the intuitive idea that anomalies are different from the typical data point.

{% content-ref url="../statistics/outliers.md" %}
[outliers.md](../statistics/outliers.md)
{% endcontent-ref %}

{% hint style="warning" %}
Under construction
{% endhint %}

### Basic methods

#### Z-Score

{% content-ref url="../statistics/z-score.md" %}
[z-score.md](../statistics/z-score.md)
{% endcontent-ref %}

#### IQR

{% content-ref url="../statistics/iqr.md" %}
[iqr.md](../statistics/iqr.md)
{% endcontent-ref %}

### Multivariate anomaly detection&#xD;

### Clustering

#### DBScan clustering

{% content-ref url="../machine-learning-algorithms/unsupervised-learning/clustering/dbscan.md" %}
[dbscan.md](../machine-learning-algorithms/unsupervised-learning/clustering/dbscan.md)
{% endcontent-ref %}

#### Other clustering techniques

These clustering techniques may be used to detect instances that are far away from clusters.

{% content-ref url="../machine-learning-algorithms/unsupervised-learning/clustering/kmeans.md" %}
[kmeans.md](../machine-learning-algorithms/unsupervised-learning/clustering/kmeans.md)
{% endcontent-ref %}

{% content-ref url="../machine-learning-algorithms/unsupervised-learning/clustering/gaussian-mixture-model.md" %}
[gaussian-mixture-model.md](../machine-learning-algorithms/unsupervised-learning/clustering/gaussian-mixture-model.md)
{% endcontent-ref %}

### Tree-based approach

#### Isolation Forest

It is an unsupervised learning algorithm that belongs to the **ensemble decision trees** family. It **explicitly isolates anomalies** instead of profiling and constructing normal points and regions **by assigning a score to each data point**.

{% hint style="success" %}
This algorithm **works great with very high dimensional datasets** and it proved to be a very effective way of detecting anomalies.
{% endhint %}

#### Robust Random Cut Forest (RCF)

{% embed url="https://youtu.be/yx1vf3uapX8" %}

