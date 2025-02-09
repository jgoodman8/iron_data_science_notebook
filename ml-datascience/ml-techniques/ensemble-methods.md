# Ensemble methods

{% hint style="info" %}
_Sources:_

* [_Ensemble methods: bagging, boosting and stacking (Joseph Rocca)_](https://towardsdatascience.com/ensemble-methods-bagging-boosting-and-stacking-c9214a10a205)
* [_Boosting, Bagging, and Stacking — Ensemble Methods with sklearn and mlens (Robert R.F. DeFilippi)_](https://medium.com/@rrfd/boosting-bagging-and-stacking-ensemble-methods-with-sklearn-and-mlens-a455c0c982de)
{% endhint %}

## Overview

This is a machine learning paradigm where **multiple&#x20;**_**weak learners**_ are trained to solve the same problem and combined to get better results. The main hypothesis is that when weak models are **correctly combined** we can **obtain more** accurate and/or **robust models**.

Most of the time, these _weak models_ perform not so well by themselves either because they have a high bias or because they have too much variance to be robust (high degree of freedom models, for example).&#x20;

{% hint style="success" %}
**The idea** of ensemble methods is to try **reducing bias or variance of such weak learners by combining several of them** together.
{% endhint %}

Notice that is important to be **coherent with the way we aggregate these models**. For instance, when selecting models with high variance, we should combine them with an aggregation method that helps to reduce variance.

{% hint style="success" %}
**The goals:**

* **Bagging** $$\Rightarrow$$ **reduces** the model’s **variance**.
* **Boosting** $$\Rightarrow$$**reduces** the model’s **bias**.
* **Stacking** $$\Rightarrow$$ **increases** the **predictive force** of a set of models.
{% endhint %}

## Bagging

* Effective method **when data is limited**.
* It **can be parallelized**.
* The main idea is to **fit several independent models** and to **average their predictions** in order to obtain a model with a lower variance.
* It generates **bootstrap samples** (representativity from the original dataset but independent from each other) to fit each model.
* There are several possible ways to aggregate the multiple models fitted in parallel:
  * For a regression problem, we can literally **average the outputs**.
  * For classification, we can consider:
    * &#x20;a **hard-voting** system: each model output is a vote, and the class with more votes is returned.
    * a **soft-voting** system: models return probabilities and the class with the highest averaged probability is returned.

![](<../../.gitbook/assets/image (56).png>)

{% content-ref url="../machine-learning-algorithms/supervised-learning/classification-algorithms/random-forest.md" %}
[random-forest.md](../machine-learning-algorithms/supervised-learning/classification-algorithms/random-forest.md)
{% endcontent-ref %}

## Boosting

Consists in **fitting SEQUENTIALLY multiple weak learners** in a very adaptative way:

* Each model in the sequence is fitted giving **more importance to observations in the dataset that were badly handled by the previous models** in the sequence.
* &#x20;So, each new model **focuses its efforts on the most difficult observations** to fit.

{% hint style="success" %}
At the end of the process, we get a **strong learner with a LOWER BIAS**
{% endhint %}

* Base models that are often considered for boosting are **models with a low variance but high bias**.
* This method **cannot be parallelized**.

![](<../../.gitbook/assets/image (33).png>)

{% content-ref url="../machine-learning-algorithms/supervised-learning/adaptative-boosting.md" %}
[adaptative-boosting.md](../machine-learning-algorithms/supervised-learning/adaptative-boosting.md)
{% endcontent-ref %}

{% content-ref url="../machine-learning-algorithms/supervised-learning/gradient-boosting.md" %}
[gradient-boosting.md](../machine-learning-algorithms/supervised-learning/gradient-boosting.md)
{% endcontent-ref %}

## Stacking

* It may train **multiple heterogeneous learners**.
* It combines their outputs using a **meta-learner** to output final predictions **based on the multiple predictions** returned by these weak models.

![](<../../.gitbook/assets/image (98).png>)

{% hint style="warning" %}
"Keep in mind just by adding layers and more models to your stacking algorithm does not mean you’ll get a better predictor. There are [**no free lunches**](https://www.wikiwand.com/en/No_free_lunch_theorem) **in machine learning**."
{% endhint %}
