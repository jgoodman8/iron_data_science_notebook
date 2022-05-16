# Ridge vs Lasso

{% hint style="info" %}
_Credit:_

* __[_Regularization in Machine Learning (Prashant Gupta)_](https://towardsdatascience.com/regularization-in-machine-learning-76441ddcf99a)__
* __[_L1 and L2 Regularization Methods_ _(Anuja Nagpal)_](https://towardsdatascience.com/l1-and-l2-regularization-methods-ce25e7fc831c)__
{% endhint %}

## Overview

|                    Lasso                    |                    Ridge                    |
| :-----------------------------------------: | :-----------------------------------------: |
|                      L1                     |                      L2                     |
| $$loss+ \lambda \sum_{j=1}^{p} | \beta_j|$$ | $$loss + \lambda \sum_{j=1}^{p} \beta_j^2$$ |

{% content-ref url="../ml-techniques/regularization.md" %}
[regularization.md](../ml-techniques/regularization.md)
{% endcontent-ref %}

## About the equations

Both regressions can be thought of as solving an equation, where the summation of the regularized coefficients is less or equal to _s_. Where _s_ is a constant that exists for each value of shrinkage factor _λ._

* **Ridge**: $$\beta_1^2 + \beta_2^2 \le s$$.  This implies that coefficients have the smallest RSS for all points that lie within the **circle** given by the inequation.
* **Lasso**: $$|\beta_1| + |\beta_2| \le s$$. This implies that lasso coefficients have the smallest RSS for all points that lie within the **diamond** given by the inequation.

![Source: An Introduction to Statistical Learning by Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani](<../../.gitbook/assets/image (97).png>)

## Conclusions

&#x20;The **key difference** between these techniques is that **Lasso shrinks the less important feature’s coefficient to zero** thus, removing some features altogether. So, this works well for **feature selection** in case we have a **huge number of features**.

&#x20;This sheds light on the obvious **disadvantage of ridge regression**, which is **model interpretability.** Given, it will shrink **the coefficients for least important predictors, very close to zero**. But it will never make them exactly zero. In other words, the final model will include all predictors. However, in the case of the lasso, the **L1 penalty** has the eﬀect of forcing some of the **coeﬃcient estimates to be exactly equal to zero** when the tuning parameter λ is suﬃciently large. Therefore, the lasso method also performs variable selection and is said to yield sparse models.
