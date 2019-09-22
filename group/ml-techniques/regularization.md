# Regularization

{% hint style="info" %}
_Sources:_

* \_\_[_Regularization in Machine Learning \(Prashant Gupta\)_](https://towardsdatascience.com/regularization-in-machine-learning-76441ddcf99a)\_\_
* \_\_[_What is regularization in machine learning? \(Quora\)_](https://www.quora.com/What-is-regularization-in-machine-learning)
{% endhint %}

## Overview

**Avoiding overfitting** is one of the major aspects of training a machine learning model. This happens when the model adjusts to the noise in training data. Thus, the resulting model won't be flexible enough to generalize new instances. Regularization **discourages learning a more complex or flexible model**, so as to avoid the risk of overfitting. 

> For further info about overfitting and how to avoid it, check out the [_Bias-Variance Tradeoff_](../frequent-questions/bias-variance-tradeoff.md) section.

### How does it work?

Let's imagine we want to build a simple model:

* Given our training set $$X$$, we try applying a linear regression $$ y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3$$. Where each $$\beta_i$$ represents the _**coefficient estimates**_ for the different $$X_i$$ variables.
* We measure [_accuracy_](metrics.md#accuracy) regarding a [_loss metric_](loss-functions.md)_,_ known as _**residual sum of squares**_ or _RSS_. The coefficients are chosen, such that they minimize this loss function.

$$
RSS = \sum_{i=1}^{n} \left( y_i - \beta_0 - \sum_{i=1}^{p} \beta_jx_{ij} \right)^2
$$

* However, this model might be too simple. Then, we could thinkg about **adding some new features** $$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3 + ... + \beta_p x_p$$. Now the model has become more complex, but **it might tend to overfit!**
*  If there is noise in the training data, then the **estimated coefficients won’t generalize well** to the future data. This is where regularization comes in and shrinks or **regularizes these learned estimates towards zero**.

## Techniques

### Lasso

It penalizes the loss function by adding the _shrinkage quantity_. This way, the coefficients are estimated by minimizing the whole quantity. _**Lasso**_ **applies the modulus** $$| \beta_j|$$ **to every coefficient**. This is also called _**L1 regularization** or L1 norm._

$$
RSS + \lambda \sum_{j=1}^{p} | \beta_j| = \sum_{i=1}^{n} \left( y_i - \beta_0 - \sum_{i=1}^{p} \beta_jx_{ij} \right)^2 + \lambda \sum_{j=1}^{p} | \beta_j|
$$

Here, **λ is the regularization parameter** that decides **how much we want to penalize** the flexibility of our model. The increase in flexibility of a model is represented by increase in its coefficients, and if we want to minimize the above function, then these coefficients need to be small. 

 _When **λ = 0, the penalty term has no**_ **eﬀect**, and the estimates produced by ridge regression will be equal to least squares. However, as **λ→∞**, the impact of the shrinkage **penalty grows**.

### Ridge

As _lasso_ does, it penalizes the loss function by adding the _shrinkage quantity_. It's also parametrized by the **λ is the regularization parameter**. However, _**ridge**_ **applies the square** $$\beta_j^2$$ **to every coefficient**. It's also called _**L2 regularization**_ or _L2 norm._

$$
RSS + \lambda \sum_{j=1}^{p} \beta_j^2 =
\sum_{i=1}^{n} \left( y_i - \beta_0 - \sum_{i=1}^{p} \beta_jx_{ij} \right)^2 + \lambda \sum_{j=1}^{p} \beta_j^2
$$

{% page-ref page="../frequent-questions/ridge-vs-lasso.md" %}

