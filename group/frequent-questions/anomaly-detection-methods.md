# Anomaly detection methods

{% hint style="info" %}
_Sources & credit:_

* \_\_[_What machine learning technique is usually used to solve anomaly detection? \(Quora\)_](https://www.quora.com/What-machine-learning-technique-is-usually-used-to-solve-anomaly-detection)\_\_
* \_\_[_How to use machine learning for anomaly detection and condition monitoring \(Vegard Flovik\)_](https://towardsdatascience.com/how-to-use-machine-learning-for-anomaly-detection-and-condition-monitoring-6742f82900d7)\_\_
* \_\_[_5 Ways to Detect Outliers/Anomalies That Every Data Scientist Should Know \(Will Badr\)_](https://towardsdatascience.com/5-ways-to-detect-outliers-that-every-data-scientist-should-know-python-code-70a54335a623)\_\_
* \_\_[_A Brief Overview of Outlier Detection Techniques \(Sergio Santoyo\)_](https://towardsdatascience.com/a-brief-overview-of-outlier-detection-techniques-1e0b2c19e561)\_\_
* \_\_[_Intuitively Understanding Variational Autoencoders \(Irhum Shafkat\)_](https://towardsdatascience.com/intuitively-understanding-variational-autoencoders-1bfe67eb5daf)\_\_
{% endhint %}

Depending on the **presence or lack of labels**, there are two approaches to face yourself to an anomaly detection problem.

## As an unbalanced classification problem

When we are given a set of observations with labels that indicate whether each point is an anomaly or not, this can be focus as a **binary classification problem**. So we can use any classifier we like. The only issue here is that **anomalies are by definition rare events**, so you’ll have to deal with class imbalance.

{% page-ref page="how-to-deal-with-unbalanced-datasets.md" %}

## As an unsupervised problem

In this scenary, we are given  a **set of points without class labels**. Some of them are anomalies and some aren’t, but you don’t know which is which. The goal here is to operationalize the intuitive idea that anomalies are different from the typical data point.

{% hint style="warning" %}
Under construction
{% endhint %}

### Basic methods

#### Standard deviation

#### Boxplots

#### Z-Score or Extreme Value Analysis

### Multivariate anomaly detection

### Clustering

#### KMeans + Mahalanobis distance

#### DBScan clustering

### Isolation Forest

### Robust Random Cut Forest \(RCF\)

### Variational Autoencoders



