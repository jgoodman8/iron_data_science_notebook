# Anomaly detection methods

{% hint style="info" %}
_Sources & credit:_

* \_\_[_What machine learning technique is usually used to solve anomaly detection? \(Quora\)_](https://www.quora.com/What-machine-learning-technique-is-usually-used-to-solve-anomaly-detection)\_\_
* \_\_[_How to use machine learning for anomaly detection and condition monitoring \(Vegard Flovik\)_](https://towardsdatascience.com/how-to-use-machine-learning-for-anomaly-detection-and-condition-monitoring-6742f82900d7)\_\_
* \_\_[_5 Ways to Detect Outliers/Anomalies That Every Data Scientist Should Know \(Will Badr\)_](https://towardsdatascience.com/5-ways-to-detect-outliers-that-every-data-scientist-should-know-python-code-70a54335a623)\_\_
* \_\_[_A Brief Overview of Outlier Detection Techniques \(Sergio Santoyo\)_](https://towardsdatascience.com/a-brief-overview-of-outlier-detection-techniques-1e0b2c19e561)\_\_
* \_\_[_Intuitively Understanding Variational Autoencoders \(Irhum Shafkat\)_](https://towardsdatascience.com/intuitively-understanding-variational-autoencoders-1bfe67eb5daf)\_\_
* \_\_[_DBSCAN: What is it? When to use it? How to use it?_](https://medium.com/@elutins/dbscan-what-is-it-when-to-use-it-how-to-use-it-8bd506293818)
* \_\_[_Best clustering algorithms for anomaly detection_](https://towardsdatascience.com/best-clustering-algorithms-for-anomaly-detection-d5b7412537c8)\_\_
{% endhint %}

Depending on the **presence or lack of labels**, there are two approaches to face yourself to an anomaly detection problem.

## As an unbalanced classification problem

When we are given a set of observations with labels that indicate whether each point is an anomaly or not, this can be focus as a **binary classification problem**. So we can use any classifier we like. The only issue here is that **anomalies are by definition rare events**, so you’ll have to deal with class imbalance.

{% page-ref page="how-to-deal-with-imbalanced-datasets.md" %}

## As an unsupervised problem

In this scenario, we are given  a **set of points without class labels**. Some of them are anomalies and some aren’t, but you don’t know which is which. The goal here is to operationalize the intuitive idea that anomalies are different from the typical data point.

{% page-ref page="../statistics/outliers.md" %}

{% hint style="warning" %}
Under construction
{% endhint %}

### Basic methods

#### Z-Score

Also known as _standard score of an observation_, this method assumes data follows a gaussian distribution.

{% hint style="danger" %}
It's a parametric method which indicates **how many standard deviations** an instance is **from the sample’s mean**.
{% endhint %}

![](../../.gitbook/assets/image%20%2832%29.png)

The z-score of every data point is calculated using the formula: $$z = (x-\mu)/\sigma$$. It can be easily calculated using the method provided by [sklearn](https://docs.scipy.org/doc/scipy-0.17.0/reference/generated/scipy.stats.zscore.html).

Once every z-score is computed, **outliers are detected given a threshold**. It's usually set to: $$2.5$$, $$3.0$$ or $$3.5$$.

#### IQR

Assuming data follows a gaussian distribution, the IQR covers the **range between the Q1 and Q3**. It's very easily to compute: $$\text{IQR} = \text{Q3} - \text{Q1}$$.

Once the IQR is known, we can classify as anomaly every value:

* Higher than $$Q3 + 1.5 \text{ IQR}$$
* Lower than $$Q1 - 1.5 \text{ IQR}$$

![Credit: Wikipedia](../../.gitbook/assets/image%20%2828%29.png)

### Multivariate anomaly detection

### Clustering

#### DBScan clustering

It is parametrized by:

* _eps_ $$\Rightarrow$$ **maximum distance** between two points to consider them as neighbors.
* _min\_points_ $$\Rightarrow$$ **minimum number of points** to form a cluster.



![](../../.gitbook/assets/image%20%2895%29.png)

#### Other clustering techniques

These clustering techniques may be used to detect instances that are far away from clusters.

{% page-ref page="../machine-learning-algorithms/unsupervised-learning/clustering/kmeans.md" %}

{% page-ref page="../machine-learning-algorithms/unsupervised-learning/clustering/gaussian-mixture-model.md" %}

### Tree-based approach

#### Isolation Forest

It is an unsupervised learning algorithm that belongs to the **ensemble decision trees** family. It **explicitly isolates anomalies** instead of profiling and constructing normal points and regions **by assigning a score to each data point**.

{% hint style="success" %}
This algorithm **works great with very high dimensional datasets** and it proved to be a very effective way of detecting anomalies.
{% endhint %}

#### Robust Random Cut Forest \(RCF\)

{% embed url="https://youtu.be/yx1vf3uapX8" %}



