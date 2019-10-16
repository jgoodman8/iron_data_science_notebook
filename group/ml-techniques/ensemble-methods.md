# Ensemble methods

{% hint style="info" %}
_Sources:_

* \_\_[_Ensemble methods: bagging, boosting and stacking \(Joseph Rocca\)_](https://towardsdatascience.com/ensemble-methods-bagging-boosting-and-stacking-c9214a10a205)
* \_\_[_Boosting, Bagging, and Stacking — Ensemble Methods with sklearn and mlens \(Robert R.F. DeFilippi\)_](https://medium.com/@rrfd/boosting-bagging-and-stacking-ensemble-methods-with-sklearn-and-mlens-a455c0c982de)\_\_
{% endhint %}

## Overview

Thi is a machine learning paradigm where **multiple** _**weak learners**_ are trained to solve the same problem and combined to get better results. The main hypothesis is that when weak models are **correctly combined** we can obtain more accurate and/or robust models.

Most of the time, these _weak models_ perform not so well by themselves either because they have a high bias or because they have too much variance to be robust \(high degree of freedom models, for example\). Then, **the idea of ensemble methods is to try reducing bias or variance of such weak learners by combining several of them** together.

Usually **a single base learning algorithm** is used so that we have homogeneous weak learners that are **trained in different ways**. But, notice that is important to be **coherent with the way we aggregate these models**. Thus,  when we choose **models with a high variance**, we should combine them with an **aggregating method that tends to reduce variance**.

### Methods goals

* **Bagging** to decrease the model’s variance
* **Boosting** to decreasing the model’s bias
* **Stacking** to increasing the predictive force of the classifier.

## Bagging

* Effective method **when data is limited**.
* It **can be parallelized**.
* The main idea is to **fit several independent models and average their predictions** in order to obtain a model with a lower variance.
* It generates **bootstrap samples** \(representativity from the origin dataset but independente from each other\) to fit each models.
* There are several possible ways to aggregate the multiple models fitted in parallel:
  * For a regression problem, the outputs can be literally averaged.
  * For classification, we can consider:
    *  a **hard-voting** system: each model output is a vote, and the class with more votes is returned.
    * a **soft-voting** system: models returns probabilities and the class with the highest averaged probability is returned.

![](../../.gitbook/assets/image%20%2855%29.png)

{% page-ref page="../machine-learning-algorithms/supervised-learning/classification-algorithms/random-forest.md" %}

## Boosting



## Stacking







