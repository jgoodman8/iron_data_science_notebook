# How does a ROC curve work?

{% hint style="info" %}
Source:

* \_\_[_Understanding AUC-ROC curve \(Sarang Narkhede\)_](https://towardsdatascience.com/understanding-auc-roc-curve-68b2303cc9c5)\_\_
* \_\_[_How and When to Use ROC Curves and Precision-Recall Curves for Classification in Python \(Jaon Browniee\)_](https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/)\_\_
* \_\_[_Beyond Accuracy: Precision and Recall \(Will Koehrsen\)_](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c)\_\_
{% endhint %}

## Overview

* **ROC** \(Receiver Operating Characteristics\) is a **probability curve**.
* **AUC** \(Area Under the Curve\) represents degree or measure of separability.
* **AUC-ROC** is a **performance measurement** for classification problem **at various thresholds settings**.
* Range: \[0, 1\]
  * Best: 1
  * Worst: 0.5
  * Inverse: 0

![Image courtesy: My Photoshopped Collection](../../.gitbook/assets/image%20%2846%29.png)

{% hint style="success" %}
An ROC curve plots the **TPR on the y-axis versus the FPR on the x-axis**. The TPR is the **recall** and the FPR is the **probability of a false alarm**.
{% endhint %}

## Understanding the probability curves

When two **distributions overlap**, we introduce **type 1 and type 2 error**. Depending upon the **threshold**, we can **minimize or maximize them**. A threshold equal to 0.5 will imply the metric we give an equal weight to the sensitivity and specificity of the model.

When we **decrease the threshold**, we get more positive values thus it **increases the** [**recall**](../ml-techniques/metrics.md#recall) **and decreasing the** [**specificity**](../ml-techniques/metrics.md#specificity). Similarly, when we increase the threshold, we get more negative values thus we get higher specificity and lower recall.

{% tabs %}
{% tab title="AUC\_ROC = 1" %}
In the **ideal situation**, distribution curve of the **positive class is equal** to the distribution of the **negative** one.

![](../../.gitbook/assets/image%20%2829%29.png)
{% endtab %}

{% tab title="AUC\_ROC = 0.7" %}
![](../../.gitbook/assets/image%20%288%29.png)
{% endtab %}

{% tab title="AUC\_ROC = 0.5" %}
When AUC is approximately 0.5, model has **no discrimination capacity** to distinguish between positive class and negative class.

![](../../.gitbook/assets/image%20%2895%29.png)
{% endtab %}

{% tab title="AUC\_ROC = 0" %}
When AUC is approximately 0, model is **actually reciprocating the classes**. It means, model is predicting negative class as a positive class and vice versa.

![](../../.gitbook/assets/image%20%2827%29.png)
{% endtab %}
{% endtabs %}

{% hint style="success" %}
 Finally, we can quantify a model’s ROC curve by calculating the total [Area Under the Curve \(AUC\)](https://en.wikipedia.org/wiki/Receiver_operating_characteristic#Area_under_the_curve).
{% endhint %}

To make this clear:

* Smaller values on the x-axis of the plot indicate lower false positives and higher true negatives.
* Larger values on the y-axis of the plot indicate higher true positives and lower false negatives.

### Dealing with multiclass models

Using One vs All methodology,  we can plot _N_ number of AUC-ROC Curves for the given _N_ number classes.

