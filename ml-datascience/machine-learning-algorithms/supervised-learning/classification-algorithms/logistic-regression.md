# Logistic Regression

### Binary logistic regression

{% hint style="warning" %}
* Converges to **minimum loss** but will **just draw linearly boundaries** on data
* Can only handle 2 classes
{% endhint %}

Main characteristics

* Binary Classification Model
* Probabilistic output (0. - 1.)
* **Cannot use non-linear decision boundaries**
* Uses [#sigmoid-or-logistic-function](../../../ml-techniques/activation-functions.md#sigmoid-or-logistic-function "mention") as the activation function
* [#threshold-function](../../../ml-techniques/selection-functions.md#threshold-function "mention") used to pick a discrete binary output



Relevant properties:

* Assumes:
  * linearity between features and log-odds
  * independent observations
  * minimal multicollinearity
* Supports [#lasso-l1](../../../ml-techniques/regularization.md#lasso-l1 "mention") and [#ridge-l2](../../../ml-techniques/regularization.md#ridge-l2 "mention") regularization to prevent overfitting.
* Weight coefficients are **interpretable**

<figure><img src="../../../../.gitbook/assets/image (130).png" alt=""><figcaption></figcaption></figure>

### Multiclass Logistic Regression

{% hint style="info" %}
* Can handle **multiple classes**
* But it **just can use linear boundaries** to separate data
{% endhint %}



Also known as **Softmax Regression Model** or **Multinomial Logistic Regression**:

* [#softmax](../../../ml-techniques/activation-functions.md#softmax "mention") activation, instead of [#sigmoid-or-logistic-function](../../../ml-techniques/activation-functions.md#sigmoid-or-logistic-function "mention")
* One-hot Encoded labels, instead of 0/1 labels
* Multiclass Cross Entropy, instead of [#binary-cross-entropy](../../../ml-techniques/loss-functions.md#binary-cross-entropy "mention") as the loss function

<figure><img src="../../../../.gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>
