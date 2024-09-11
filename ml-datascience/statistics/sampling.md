# Sampling

{% hint style="info" %}
_Sources:_

* [_Methods of sampling from a population (Health Knowledge)_](https://www.healthknowledge.org.uk/public-health-textbook/research-methods/1a-epidemiology/methods-of-sampling-population)
* [_Sampling Techniques (Seema Singh)_](https://towardsdatascience.com/sampling-techniques-a4e34111d808)
* [_A Gentle Introduction to Statistical Sampling and Resampling_](https://machinelearningmastery.com/statistical-sampling-and-resampling/)
* [_Statistical Learning (II): Data Sampling & Resampling_](https://towardsdatascience.com/statistical-learning-ii-data-sampling-resampling-93a0208d6bb8)
{% endhint %}

## Sampling

> _Sampling consists of selecting some part of the population to observe so that one may estimate something about the whole population._

![](<../../.gitbook/assets/image (108).png>)

{% hint style="success" %}
**Probability vs Non-probability sampling**

* The difference is whether the **sample picking is based on randomization or not**.
* With randomization, every element gets an equal chance to be picked up and to be part of the sample.
{% endhint %}

### Statistical Sampling

#### Simple Random Sampling

* Every element has an **equal chance of getting selected** to be the part sample.&#x20;
* It is used when we do **not have any kind of prior information** about the target population.

#### Stratified Sampling

* Elements of the population are divided into small subgroups based on similarity (ie data labels or classes).
* The **subset is selected from every group or class** based on the percentage accounting for the overall population.
* We **need to have prior information** about the population to create subgroups.

#### Cluster Sampling

* The entire population is divided into clusters and then the **clusters are randomly selected**.
* Clusters are created or identified based on features.
* Sub-types:
  * _**Single Stage Cluster Sampling**:_ the whole cluster is selected.
  * _**Two-Stage Cluster Sampling:**_ elements from picked clusters are randomly selected.

### Non-probability Sampling

This technique is more reliant on the researcher’s ability to select elements for a sample. The outcome of the sampling might be biased and makes it more difficult for all the elements of the population to be part of the sample equally.

## Resampling techniques

Statistical resampling methods are procedures that describe **how to economically use available data** to estimate a population parameter. The result can be both a more accurate estimate of the parameter (such as taking the mean of the estimates) and a quantification of the uncertainty of the estimate (such as adding a confidence interval).

### Bootstrapping

It is a resampling method by **independently sampling with replacement from an existing sample data** with same sample size n, and performing inference among these resampled data.

Steps:

1. Get a sample from a population with sample size n.
2. Draw a sample from the original sample data **with replacement** with size n, and replicate B times, each re-sampled sample is called a Bootstrap Sample, and t**here will totally B Bootstrap Samples**.
3. Evaluate the **statistic** of _**θ**_** for each Bootstrap Sample**, and there will be totally B estimates of _θ_.
4. Construct a **sampling distribution** with these B Bootstrap statistics and use it to make a further statistical inference, such as:
   * Estimating the standard error of statistics for _θ._
   * Obtaining a Confidence Interval for _θ_.

![](<../../.gitbook/assets/image (110).png>)

### **K-Fold Cross-Validation**

* Dataset is partitioned into K groups.
* K-1 groups are assigned to training and the remaining one for testing.
* Useful when the training dataset is fairly small.
* **To avoid overfitting**!

### Oversampling & Undersampling

* Given **imbalanced datasets**, the problem we often face is where **most data falls into the major class**, whereas a few data falls into the minority class.&#x20;
* To overcome the poor performance of model training for such imbalanced data, over-sampling and under-sampling techniques are primarily suggested to produce equally distributed data fall into each class.

![](<../../.gitbook/assets/image (109).png>)
