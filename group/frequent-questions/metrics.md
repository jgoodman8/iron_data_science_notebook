# Metrics

{% hint style="info" %}
_Sources:_

* \_\_[_Understanding confusion matrix \(Sarang Narkhede\)_](https://towardsdatascience.com/understanding-confusion-matrix-a9ad42dcfd62)\_\_
{% endhint %}

## The confusion matrix

Confusion Matrix is a **performance measurement** for machine learning **classification** where output can be **two or more classes**.

* **True positive**
  * Predicted 1 $$\Rightarrow$$ Actual 1
* **True negative**
  * Predicted 1 $$\Rightarrow$$ Actual 0
  * This is a _**Type-1 Error**_
* **False negative**
  * Predicted 0 $$\Rightarrow$$ Actual 1
  * This is a _**Type-2 Error**_
* **True negative**
  * Predicted 0 $$\Rightarrow$$ Actual 0

![](../../.gitbook/assets/image%20%2826%29.png)

## Precision

From all the predicted positives, it measures how many are actually positive.

// TODO: Picture

$$
Precision = \frac{\text{TP}}{\text{TP} + \text{FP}}
$$

## Recall, Sensitivity or TPR \(True Positive Rate\)

From all the actual positives, it measures how many are classified as positives values.

// TODO: Add picture

$$
Recall = \text{TPR } = Sensitivity = \frac{\text{TP}}{\text{TP} + \text{FN}}
$$

## Specificity

// TODO: Add picture

$$
Specificity = \frac{\text{TN}}{\text{TN} + \text{FP}}
$$

## FPR \(False Positive Rate\)

$$
\text{FPR} = 1-Specificity = \frac{\text{FP}}{\text{TN} + \text{FP}}
$$

## 

