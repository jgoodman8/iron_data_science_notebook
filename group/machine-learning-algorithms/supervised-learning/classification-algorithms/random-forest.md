# Random Forest

{% hint style="info" %}
_Sources:_

* \_\_[_Ensemble methods: bagging, boosting and stacking \(Joseph Rocca\)_](https://towardsdatascience.com/ensemble-methods-bagging-boosting-and-stacking-c9214a10a205)
{% endhint %}

## Overview

The **random forest** approach is a [**bagging**](../../../ml-techniques/ensemble-methods.md#bagging) **method** where **deep trees**, fitted on **bootstrap samples**, are combined to produce an **output with lower variance**.

Addicionally, RF use another trick to make the multiple fitted trees a bit less correlated with each other: when growing each tree, instead of only sampling over the observations in the dataset to generate a bootstrap sample, we also **sample over features** and keep only a **random subset** of them to build the tree.

{% hint style="danger" %}
**Bagging + Feature sampling**
{% endhint %}

This way, all trees do not look at the exact same information to make their decisions and it **reduces the correlation** between the different returned outputs and generates a model more robust to missing data.

