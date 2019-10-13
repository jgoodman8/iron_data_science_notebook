# Metrics

{% hint style="info" %}
_Sources:_

* \_\_[_Understanding confusion matrix \(Sarang Narkhede\)_](https://towardsdatascience.com/understanding-confusion-matrix-a9ad42dcfd62)\_\_
* \_\_[_Accuracy, Precision, Recall or F1? \(Koo Ping Shung\)_](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)\_\_
* \_\_[_Cost Matrix \(IBM Knowledge Center\)_](https://www.ibm.com/support/knowledgecenter/da/SSEPGG_9.7.0/com.ibm.im.model.doc/c_cost_matrix.html)\_\_
{% endhint %}

## In regression

{% hint style="warning" %}
**TODO**
{% endhint %}

## In classification

### The confusion matrix

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

![](../../.gitbook/assets/image%20%2852%29.png)

#### Cost matrix

A cost matrix \(**error matrix**\) is also useful **when specific classification errors are more severe than others**. The Classification mining function tries to avoid classification errors with a high error weight. The trade-off of avoiding 'expensive' classification errors is an increased number of 'cheap' classification errors.

### Accuracy

From all the total samples, it measures the well-classified rate.

{% tabs %}
{% tab title="Formula" %}
$$
Accuracy = \frac{\text{TP} + \text{TN} }{Total}
$$
{% endtab %}

{% tab title="Example with sklearn" %}
It may be computed using [scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html):

```python
from sklearn.metrics import accuracy_score

y_pred = [0, 2, 1, 3]
y_true = [0, 1, 2, 3]
accuracy_score(y_true, y_pred)
>>> 0.5
```
{% endtab %}
{% endtabs %}

### Precision

From all the predicted positives, it measures the rate actually classified as positive.

{% hint style="success" %}
It is a good measure to determine, **when the costs of False Positive is high**. For instance, email spam detection.
{% endhint %}

{% tabs %}
{% tab title="Main" %}
![](../../.gitbook/assets/image%20%2850%29.png)
{% endtab %}

{% tab title="Formula" %}
$$
Precision = \frac{\text{TP}}{\text{TP} + \text{FP}}
$$
{% endtab %}

{% tab title="Example with sklearn" %}
It may be computed using [scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html):

```python
from sklearn.metrics import precision_score

precision_score(y_true, y_pred, average='weighted')
```
{% endtab %}
{% endtabs %}

### Recall

 From all the actual positives, it measures the rate classified as positives values. As well. it is called _**Sensitivity** or **True Positive Rate \(TPR\)**_.

{% hint style="success" %}
It is a good metric to select our best model **when there is a high cost associated with False Negative**. For instance, in fraud detection or sick patient detection.
{% endhint %}

{% tabs %}
{% tab title="Main" %}
![](../../.gitbook/assets/image%20%2879%29.png)
{% endtab %}

{% tab title="Formula" %}
$$
Recall = \text{TPR } = Sensitivity = \frac{\text{TP}}{\text{TP} + \text{FN}}
$$
{% endtab %}

{% tab title="Example with sklearn" %}
It may be computed using [scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html):

```python
from sklearn.metrics import recall_score

recall_score(y_true, y_pred, average='weighted')
```
{% endtab %}
{% endtabs %}

### Minimizing False Positives

![](../../.gitbook/assets/image%20%2810%29.png)

#### Specificity

From all the actual negative values, it measures the rate classified as negative.

$$
Specificity = \frac{\text{TN}}{\text{TN} + \text{FP}}
$$

#### False Positive Rate \(FPR\)

From all the actual negative values, it measures the rate misclassified as negative. It the negated probability of [specificity](metrics.md#specificity).

$$
\text{FPR} = 1-Specificity = \frac{\text{FP}}{\text{TN} + \text{FP}}
$$

### F-Score

F1 Score might be a better measure to use if we need to seek a **balance between Precision and Recall** AND there is an uneven class distribution \(large number of Actual Negatives\).

{% tabs %}
{% tab title="Formula" %}
$$
\text{F1} = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}
$$
{% endtab %}

{% tab title="Example with sklearn" %}
```python
from sklearn.metrics import f1_score

f1_score(y_true, y_pred, average='weighted')
```
{% endtab %}
{% endtabs %}



