# How does a ROC curve work?

{% hint style="info" %}
Source:

* __[_Understanding AUC-ROC curve (Sarang Narkhede)_](https://towardsdatascience.com/understanding-auc-roc-curve-68b2303cc9c5)__
* __[_How and When to Use ROC Curves and Precision-Recall Curves for Classification in Python (Jaon Browniee)_](https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/)__
* __[_Beyond Accuracy: Precision and Recall (Will Koehrsen)_](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)__
{% endhint %}

## Overview

* **ROC** (Receiver Operating Characteristics) is a **probability curve**.
* **AUC** (Area Under the Curve) represents the degree or measure of separability.
* **AUC-ROC** is a **performance measurement** for classification problems **at various thresholds settings**.
* Range: \[0, 1]
  * Best: 1
  * Worst: 0.5
  * Inverse: 0

![Image courtesy: My Photoshopped Collection](<../../.gitbook/assets/image (47).png>)

{% hint style="success" %}
A ROC curve plots the **TPR on the y-axis versus the FPR on the x-axis**. The TPR is the **recall** and the FPR is the **probability of a false alarm**.
{% endhint %}

## Understanding the probability curves

When two **distributions overlap**, we introduce **type 1 and type 2 errors**. Depending upon the **threshold**, we can **minimize or maximize them**. A threshold equal to 0.5 will imply the metric we give an equal weight to the sensitivity and specificity of the model.

When we **decrease the threshold**, we get more positive values thus it **increases the** [**recall**](../ml-techniques/metrics.md#recall) **and decreasing the** [**specificity**](../ml-techniques/metrics.md#specificity). Similarly, when we increase the threshold, we get more negative values thus we get higher specificity and lower recall.

{% tabs %}
{% tab title="AUC_ROC = 1" %}
In the **ideal situation**, the distribution curve of the **positive class is equal** to the distribution of the **negative** one.

![](<../../.gitbook/assets/image (29).png>)
{% endtab %}

{% tab title="AUC_ROC = 0.7" %}
![](<../../.gitbook/assets/image (8).png>)
{% endtab %}

{% tab title="AUC_ROC = 0.5" %}
When AUC is approximately 0.5, the model has **no discrimination capacity** to distinguish between positive class and negative class.

![](<../../.gitbook/assets/image (99).png>)
{% endtab %}

{% tab title="AUC_ROC = 0" %}
When AUC is approximately 0, the model is **actually reciprocating the classes**. It means the model is predicting a negative class as a positive class and vice versa.

![](<../../.gitbook/assets/image (27).png>)
{% endtab %}
{% endtabs %}

{% hint style="success" %}
&#x20;Finally, we can quantify a model’s ROC curve by calculating the total [Area Under the Curve (AUC)](https://en.wikipedia.org/wiki/Receiver\_operating\_characteristic#Area\_under\_the\_curve).
{% endhint %}

To make this clear:

* Smaller values on the x-axis of the plot indicate lower false positives and higher true negatives.
* Larger values on the y-axis of the plot indicate higher true positives and lower false negatives.

### Dealing with multiclass models

Using the _One-vs-All_ methodology,  we can plot _N_ AUC-ROC curves for the given _N_ classes.
