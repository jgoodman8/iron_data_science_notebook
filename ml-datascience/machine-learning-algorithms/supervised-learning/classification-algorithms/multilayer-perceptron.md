# Multilayer Perceptron

{% hint style="warning" %}
* Can **draw complex non-linear** boundaries to separate data
* But needs more data!
{% endhint %}

* Fully-connected feedforward neural network
* In the **output layer**:
  * For classification, [#softmax](../../../ml-techniques/activation-functions.md#softmax "mention") is commonly used (even for binary classification problems)
  * However, [#sigmoid-or-logistic-function](../../../ml-techniques/activation-functions.md#sigmoid-or-logistic-function "mention") can be used as well for 1/0 classification.
* In the **hidden layer**,
  * we need to use a **non-linear activation function**
  * we can use the [#sigmoid-or-logistic-function](../../../ml-techniques/activation-functions.md#sigmoid-or-logistic-function "mention")
  * but it's more common to use the [#relu](../../../ml-techniques/activation-functions.md#relu "mention")nowadays

<figure><img src="../../../../.gitbook/assets/image (134).png" alt=""><figcaption></figcaption></figure>

It can be seen as a [#multiclass-logistic-regression](logistic-regression.md#multiclass-logistic-regression "mention") model with Hidden layers:

<figure><img src="../../../../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Normally, [#cross-entropy](../../../ml-techniques/loss-functions.md#cross-entropy "mention") loss is used to train it!
{% endhint %}

### Wide vs Deep Networks

* In theory, an MLP with 1 hidden layer should be enough. But:
  * Needs lots of hidden units (wide & shallow)
  * **Prone to overfitting**
* A **narrow and deep MLP**:
  * needs fewer nodes and generalizes better
  * but, it's **harder to train**!

<figure><img src="../../../../.gitbook/assets/image (138).png" alt="" width="563"><figcaption></figcaption></figure>

### Initialize weights

* Cannot initialize the weights to 0, to avoid losing the power of the different hidden units.

<figure><img src="../../../../.gitbook/assets/image (139).png" alt="" width="298"><figcaption></figcaption></figure>

* Random initialization:
  * To **small and random numbers**!
  * To keep all hidden layers with different numbers
