# kNN

{% hint style="info" %}
_Sources:_

* __[_KNN (Towards Data Science)_](https://towardsdatascience.com/knn-k-nearest-neighbors-1-a4707b24bd1d)__
* __[_KNN Classification using Scikit-learn (Avinash Navlani)_](https://www.datacamp.com/community/tutorials/k-nearest-neighbor-classification-scikit-learn)__
{% endhint %}

## **How it works**

{% hint style="danger" %}
Is an [**instance-based algorithm**](../../../frequent-questions/instance-based-vs-model-based-learning.md#instance-based-learning)**.** So, there is **not training step**. Classification is directly inferred!
{% endhint %}

For every unlabeled instance (the ones to be classified):

1. It measures the **distance to every labeled sample**.
2. It **sorts** the distances incrementally.
3. It selects the **closets **_**k**_** instances**.
4. It **assigns the most frequent class** on the selected _k_ instances.

![Source: DataCamp](<../../../../.gitbook/assets/image (6).png>)
