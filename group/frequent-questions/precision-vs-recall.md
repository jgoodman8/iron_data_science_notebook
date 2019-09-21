# Precision vs Recall

{% hint style="info" %}
_Sources:_

* \_\_[_Precision vs Recall \(Shurti Saxena\)_](https://towardsdatascience.com/precision-vs-recall-386cf9f89488)
* \_\_[_Identification of Similar and Complementary Subparts in B-Rep Mechanical Models_](http://computingengineering.asmedigitalcollection.asme.org/article.aspx?articleid=2610217)\_\_
* \_\_[_Beyond Accuracy: Precision and Recall \(Will Koehrsen\)_](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)\_\_
{% endhint %}

## Overview

* [**Accuracy**](metrics.md#accuracy) express the percante of results correctly classified.
* [**Precision**](metrics.md#precision) means the percentage of your results which are relevant. 
* [**Recall**](metrics.md#recall) refers to the percentage of total relevant results correctly classified by your algorithm.

## The trade-off

We can see when our precision is 1.0 \(no _FP_\), our recall remains very low because we still have many _FN_. If we go to the other extreme and classify all inputs as negatives, we will have a recall of 1.0 but our precision will be very low and we’ll detain many innocent individuals. In other words, **as we increase precision we decrease recall and vice-versa**.

Depending on the situation, **we may maximize either precision** \(i.e. spam detection\) **or recall** \(i.e. desease detection\).

The [**confusion matrix**](metrics.md#the-confusion-matrix) is useful for quickly calculating precision and recall given the predicted labels from a model.  The other main visualization technique for showing the performance of a classification model is the [**Receiver Operating Characteristic \(ROC\) curve**](how-a-roc-curve-works.md).

![](../../.gitbook/assets/image%20%2819%29.png)

## Combining Precision and Recall

{% hint style="success" %}
If we want to create a **balanced classification model** with the optimal balance of recall and precision, then we try to **maximize the F1 score**.
{% endhint %}

In cases where we want to find an optimal blend of precision and recall we can combine the two metrics using what is called the [**F1 score**](metrics.md#f-score). It is the **harmonic mean of precision and recall** taking both metrics into account.

{% page-ref page="metrics.md" %}

 We use the harmonic mean instead of a simple average because it punishes extreme values. A classifier with a precision of 1.0 and a recall of 0.0 has a simple average of 0.5 but an F1 score of 0. 

{% page-ref page="how-a-roc-curve-works.md" %}

