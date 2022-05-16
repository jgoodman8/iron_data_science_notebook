# Naive Bayes

{% hint style="info" %}
_Sources:_

* __[_Naive Bayes (Scikit-Learn)_](https://scikit-learn.org/stable/modules/naive\_bayes.html)__
{% endhint %}

## Overview

It **assumes conditional independence** between every pair of features given the value of the class. This is why this method is called "naive".

The Bayes theorem states:

$$
P(y|x_1, ..., x_n) = \frac{P(y)P(x_1,...,x_n|y)}{P(x_1,...,x_n)}
$$

When assuming conditional independence:

$$
P(y|x_1, ..., x_n) = \frac{P(y)P(x_1,...,x_n|y)}{P(x_1,...,x_n)}
$$

So, we can use the following classification rule:

$$
\hat{y} = \arg\max_y P(y) \prod_{i=1}^{n} P(x_i \mid y)
$$

### Advantages

* NB classifiers **have worked quite well in many real-world situations**, famously document classification, sentiment analysis and spam filtering.&#x20;
* They **require a small amount of training data** to estimate the necessary parameters.
* They **can be extremely fast** compared to more sophisticated methods.

### Disadvantages

* Although NB is considered as a decent classifier, **it is known to be a bad estimator**. So their output probabilities are not to be taken too seriously.

## Types of NB classifiers

* [**Multinomial Naive Bayes**](https://towardsdatascience.com/multinomial-naive-bayes-classifier-for-text-analysis-python-8dd6825ece67)****
* ****[**Bernoulli Naive Bayes**](https://stats.stackexchange.com/questions/246101/when-to-use-bernoulli-naive-bayes)****
* ****[**Gaussian Naive Bayes**](https://medium.com/@LSchultebraucks/gaussian-naive-bayes-19156306079b)****
