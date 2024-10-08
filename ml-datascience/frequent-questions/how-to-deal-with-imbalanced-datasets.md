# How to deal with imbalanced datasets?

{% hint style="info" %}
_Sources:_

* [_Dealing with Imbalanced Data (Tara Boyle)_](https://towardsdatascience.com/methods-for-dealing-with-imbalanced-data-5b761be45a18)
* [_Having an Imbalanced Dataset? Here Is How You Can Fix I (Will Badr)_](https://towardsdatascience.com/having-an-imbalanced-dataset-here-is-how-you-can-solve-it-1640568947eb)
{% endhint %}

## Using the correct performance metric

[**Accuracy**](../ml-techniques/metrics.md#accuracy) **is not the best metric** to use when evaluating imbalanced datasets as it can be very misleading. It's better to try:

* [**Confusion Matrix**](../ml-techniques/metrics.md#the-confusion-matrix)
* [**Precision**](../ml-techniques/metrics.md#precision)
* [**Recall**](../ml-techniques/metrics.md#recall)
* [**F1**](../ml-techniques/metrics.md#f-score)

## Resampling Techniques

{% hint style="danger" %}
Always **split into test and train sets BEFORE trying to resample** techniques! And applying resample **ONLY in the training set**.
{% endhint %}

**Oversample**: by adding more copies of the minority class.

**Undersample**: by removing observations from the majority class.&#x20;

## Create synthetic samples

* **SMOTE** (Synthetic Minority Oversampling Technique): uses a **kNN algorithm** to generate new and synthetic data we can use for training our model.

## Apply an ensemble algorithm

{% content-ref url="../ml-techniques/ensemble-methods.md" %}
[ensemble-methods.md](../ml-techniques/ensemble-methods.md)
{% endcontent-ref %}
