# Regularization

{% hint style="info" %}
_Sources:_

* __[_Regularization in Machine Learning (Prashant Gupta)_](https://towardsdatascience.com/regularization-in-machine-learning-76441ddcf99a)__
* __[_What is regularization in machine learning? (Quora)_](https://www.quora.com/What-is-regularization-in-machine-learning)
{% endhint %}

## Overview

**Avoiding overfitting** is one of the major aspects of training a machine learning model. This happens when the model adjusts to the noise in training data. Thus, the resulting model won't be flexible enough to generalize new instances. Regularization **discourages learning a more complex or flexible model**, so as to avoid the risk of overfitting.&#x20;

> For further info about overfitting and how to avoid it, check out the [_Bias-Variance Tradeoff_](../frequent-questions/bias-variance-tradeoff.md) section.

### How does overfitting happen?

Let's imagine we want to build a simple model:

* Given our training set $$X$$, we try applying a linear regression $$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3$$. Where each $$\beta_i$$ represents the _**coefficient estimates**_ for the different $$x_i$$ variables.
* We measure [_accuracy_](metrics.md#accuracy) regarding a [_loss metric_](loss-functions.md)_,_ known as _**residual sum of squares**_ or _RSS_. The coefficients are chosen, such that they minimize this loss function.

$$
RSS = \sum_{i=1}^{n} \left( y_i - \beta_0 - \sum_{i=1}^{p} \beta_jx_{ij} \right)^2
$$

* However, this model might be too simple. Then, we could think about **adding some new features** $$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3 + ... + \beta_p x_p$$. Now the model has become more complex, but **it might tend to overfit!**
* &#x20;If there is noise in the training data, then the **estimated coefficients won’t generalize well** to the future data. This is where regularization comes in and shrinks or **regularizes these learned estimates towards zero**.

## Techniques

### Lasso (L1)

It penalizes the loss function by adding the _shrinkage quantity_. This way, the coefficients are estimated by minimizing the whole quantity. _ **Lasso**_** applies the modulus** $$| \beta_j|$$ **to every coefficient**. This is also called _**L1 regularization** or L1 norm._

$$
RSS + \lambda \sum_{j=1}^{p} | \beta_j| = \sum_{i=1}^{n} \left( y_i - \beta_0 - \sum_{i=1}^{p} \beta_jx_{ij} \right)^2 + \lambda \sum_{j=1}^{p} | \beta_j|
$$

Here, **λ is the regularization parameter** that decides **how much we want to penalize** the flexibility of our model. The increase in flexibility of a model is represented by increase in its coefficients, and if we want to minimize the above function, then these coefficients need to be small.&#x20;

&#x20;_When **λ = 0, the penalty term has no**_** eﬀect**, and the estimates produced by ridge regression will be equal to least squares. However, as **λ→∞**, the impact of the shrinkage **penalty grows**.

### Ridge (L2)

As _lasso_ does, it penalizes the loss function by adding the _shrinkage quantity_. It's also parametrized by the **λ is the regularization parameter**. However, _ **ridge**_** applies the square** $$\beta_j^2$$ **to every coefficient**. It's also called _**L2 regularization**_ or _L2 norm._

$$
RSS + \lambda \sum_{j=1}^{p} \beta_j^2 =
\sum_{i=1}^{n} \left( y_i - \beta_0 - \sum_{i=1}^{p} \beta_jx_{ij} \right)^2 + \lambda \sum_{j=1}^{p} \beta_j^2
$$

### L1 vs L2 norm

The image below shows differences between L1 and L2:

* Points on the ellipse share the value of _RSS_.
* Points of the green area share the values of regularization
* So, the **regression coefficient estimates** are **given** by the **ﬁrst point at which an ellipse contacts the constraint region**.

What does it mean?

* Given **L2 has a circular constraint** ($$\beta²$$), this **intersection will not generally occur on an axis**.
  * L2 regression coefficient estimates _**will be exclusively non-zero**._
* The **L1** constraint has corners on axes, so the RSS distribution **may intersect at an axis**.
  * When this occurs, **one of the coeﬃcients will equal zero.**

![](<../../.gitbook/assets/image (82).png>)

{% hint style="danger" %}
* **Ridge** (L2) will shrink **coefficients very close to zero,** but doesn't ignore any feature.
* **Lasso** (L1)  **also performs variable selection**.
{% endhint %}

### Other alternatives

We can use other techniques to reduce variance (given it's the goal of L1 and L2 regularization):

* [Bagging](ensemble-methods.md#bagging)
* Data augmentation
* Adding noise

When dealing with neural networks, we can use these techniques, as well:

* Early stopping
* Dropout

{% content-ref url="../frequent-questions/ridge-vs-lasso.md" %}
[ridge-vs-lasso.md](../frequent-questions/ridge-vs-lasso.md)
{% endcontent-ref %}
