# Precision vs Recall

{% hint style="info" %}
_Sources:_

* __[_Precision vs Recall (Shurti Saxena)_](https://towardsdatascience.com/precision-vs-recall-386cf9f89488)
* __[_Identification of Similar and Complementary Subparts in B-Rep Mechanical Models_](http://computingengineering.asmedigitalcollection.asme.org/article.aspx?articleid=2610217)__
* __[_Beyond Accuracy: Precision and Recall (Will Koehrsen)_](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)__
{% endhint %}

## Overview

* [**Accuracy**](../ml-techniques/metrics.md#accuracy) expresses the percentage of results correctly classified.
* [**Precision**](../ml-techniques/metrics.md#precision) means the percentage of your results that are relevant.&#x20;
* [**Recall**](../ml-techniques/metrics.md#recall) refers to the percentage of total relevant results correctly classified by your algorithm.

## The trade-off

We can see when our precision is 1.0 (no _FP_), our recall remains very low because we still have many _FN_. If we go to the other extreme and classify all inputs as negatives, we will have a recall of 1.0 but our precision will be very low and we’ll detain many innocent individuals. In other words, **as we increase precision we decrease recall and vice-versa**.

Depending on the situation, **we may maximize either precision** (i.e. spam detection) **or recall** (i.e. disease detection).

The [**confusion matrix**](../ml-techniques/metrics.md#the-confusion-matrix) is useful for quickly calculating precision and recall given the predicted labels from a model.  The other main visualization technique for showing the performance of a classification model is the [**Receiver Operating Characteristic (ROC) curve**](how-a-roc-curve-works.md).

![](<../../.gitbook/assets/image (23).png>)

## Combining Precision and Recall

{% hint style="success" %}
If we want to create a **balanced classification model** with the optimal balance of recall and precision, then we try to **maximize the F1 score**.
{% endhint %}

In cases where we want to find an optimal blend of precision and recall we can combine the two metrics using what is called the [**F1 score**](../ml-techniques/metrics.md#f-score). It is the **harmonic mean of precision and recall** taking both metrics into account.

{% content-ref url="../ml-techniques/metrics.md" %}
[metrics.md](../ml-techniques/metrics.md)
{% endcontent-ref %}

&#x20;We use the harmonic mean instead of a simple average because it punishes extreme values. A classifier with a precision of 1.0 and a recall of 0.0 has a simple average of 0.5 but an F1 score of 0.&#x20;

{% content-ref url="how-a-roc-curve-works.md" %}
[how-a-roc-curve-works.md](how-a-roc-curve-works.md)
{% endcontent-ref %}
