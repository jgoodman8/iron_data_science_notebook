# Ensemble methods

{% hint style="info" %}
_Sources:_

* \_\_[_Ensemble methods: bagging, boosting and stacking \(Joseph Rocca\)_](https://towardsdatascience.com/ensemble-methods-bagging-boosting-and-stacking-c9214a10a205)
* \_\_[_Boosting, Bagging, and Stacking — Ensemble Methods with sklearn and mlens \(Robert R.F. DeFilippi\)_](https://medium.com/@rrfd/boosting-bagging-and-stacking-ensemble-methods-with-sklearn-and-mlens-a455c0c982de)\_\_
{% endhint %}

## Overview

This is a machine learning paradigm where **multiple** _**weak learners**_ are trained to solve the same problem and combined to get better results. The main hypothesis is that when weak models are **correctly combined** we can obtain more accurate and/or robust models.

Most of the time, these _weak models_ perform not so well by themselves either because they have a high bias or because they have too much variance to be robust \(high degree of freedom models, for example\). 

{% hint style="info" %}
**The idea** of ensemble methods is to try **reducing bias or variance of such weak learners by combining several of them** together.
{% endhint %}

Notice that is important to be **coherent with the way we aggregate these models**. In example,  when we choose models with a high variance, we should combine them with an aggregating method that tends to reduce variance.

{% hint style="success" %}
**The goals:**

* **Bagging** $$\Rightarrow$$ **reduce** the model’s **variance**.
* **Boosting** $$\Rightarrow$$**reduce** the model’s **bias**.
* **Stacking** $$\Rightarrow$$ **increase** the **predictive force** of a set of models.
{% endhint %}

## Bagging

* Effective method **when data is limited**.
* It **can be parallelized**.
* The main idea is to **fit several independent models** and **average their predictions** in order to obtain a model with a lower variance.
* It generates **bootstrap samples** \(representativity from the origin dataset but independente from each other\) to fit each models.
* There are several possible ways to aggregate the multiple models fitted in parallel:
  * For a regression problem, we can literally **average the outputs**.
  * For classification, we can consider:
    *  a **hard-voting** system: each model output is a vote, and the class with more votes is returned.
    * a **soft-voting** system: models returns probabilities and the class with the highest averaged probability is returned.

![](../../.gitbook/assets/image%20%2856%29.png)

{% page-ref page="../machine-learning-algorithms/supervised-learning/classification-algorithms/random-forest.md" %}

## Boosting

Consists in **fitting SEQUENTIALLY multiple weak learners** in a very adaptative way:

* Each model in the sequence is fitted giving **more importance to observations in the dataset that were badly handled by the previous models** in the sequence.
*  So, each new model **focus its efforts on the most difficult observations** to fit.

{% hint style="danger" %}
At the end of the process, we get a **strong learner with lower bias**.
{% endhint %}

* Base models that are often considered for boosting are **models with low variance but high bias**.
* This method **cannot be parallelized**.

![](../../.gitbook/assets/image%20%2833%29.png)

{% page-ref page="../machine-learning-algorithms/supervised-learning/adaptative-boosting.md" %}

{% page-ref page="../machine-learning-algorithms/supervised-learning/gradient-boosting.md" %}

## Stacking

* It may train **multiple heterogeneous learners**.
* It combines their outputs using a **meta-learner** to output final predictions **based on the multiple predictions** returned by these weak models.

![](../../.gitbook/assets/image%20%2896%29.png)

{% hint style="warning" %}
"Keep in mind just by adding layers and more models to your stacking algorithm, does not mean you’ll get a better predictor. There are [**no free lunches**](https://www.wikiwand.com/en/No_free_lunch_theorem) **in machine learning**."
{% endhint %}

