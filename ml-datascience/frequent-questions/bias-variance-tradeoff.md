# Bias-Variance Tradeoff

{% hint style="info" %}
_More reading:_ [_Bias-Variance Tradeoff (Wikipedia)_](https://en.wikipedia.org/wiki/Bias-variance_tradeoff)
{% endhint %}

![](<../../.gitbook/assets/image (64).png>)

## What is the bias error?

{% hint style="success" %}
Bias is the error a model makes **in making too simple guesses** about the data. For example, if you use a linear regression to capture a non-linear pattern, the model won't learn well, no matter how much data is available. This is called **underfitting**.
{% endhint %}

In statistics, an estimator's bias (or **bias function**) is the **difference between the estimator's expected value and the true value** of the instance being estimated. An estimator or decision rule with zero bias is called **unbiased.** So, it measures the difference between the estimated value by a model or measurement method and the real one.

![The bias is expressed as the systematic error](../../.gitbook/assets/illustration-of-precision-error-and-bias-error-reprinted-with-minor-changes-from-asme.png)

**Bias** refers to the difference between the true or correct value of some quantity and the measurement or estimate of that quantity. In principle, it cannot be calculated therefore unless that true or correct value is known, although this problem bites to varying degrees.

* In the simplest kind of problem, the true value is known (as when the center of a target is visible and the distance of a shot from the center can be measured; this is a common analogy) and bias is then usually calculated as the difference between the true value and the mean (or occasionally some other summary) of measurements or estimates.
* In other problems, some careful method is regarded as the state of the art and so yielding the best possible measurements, and so other methods are regarded as more or less biased according to their degree of systematic departure from the best method (in some fields termed a gold standard).
* In yet other problems, we have one or more methods all deficient to some degree, and assessment of bias is then difficult or impossible. It is then tempting, or possibly even natural, to change the question and judge truth according to consistency between methods.

## What is variance error?

{% hint style="success" %}
Variance is the error produced when the **model adapts too well to training data**, **capturing even the noise**. This makes it too sensitive to small changes in the data. This is called **overfitting**.
{% endhint %}

Variance is the variability of model predictions for a given data point or a value that tells us the spread of our data. A model with **high variance pays** a lot of **attention to training data and** does **not generalize to unseen data**. As a result, such models **perform very well on training data** but have **high error rates on test data**.

## Bias vs Variance

This **tradeoff** is the property of a set of predictive models whereby models with a lower [bias](https://en.wikipedia.org/wiki/Bias_of_an_estimator) in [parameter](https://en.wikipedia.org/wiki/Statistical_parameter) [estimation](https://en.wikipedia.org/wiki/Estimation_theory) have a higher [variance](https://en.wikipedia.org/wiki/Variance) of the parameter estimates across [samples](https://en.wikipedia.org/wiki/Sample_\(statistics\)) and vice versa. The **bias-variance dilemma** or **problem** is the conflict in trying to simultaneously minimize these two sources of [error](https://en.wikipedia.org/wiki/Errors_and_residuals_in_statistics) that prevent [supervised learning](https://en.wikipedia.org/wiki/Supervised_learning) algorithms from generalizing beyond their [training set](https://en.wikipedia.org/wiki/Training_set).

![Relation with overfit and underfit](../../.gitbook/assets/bias_var.png)

A high **bias** error is due to erroneous or overly **simplistic assumptions in the learning algorithm** you’re using. This can lead to the model **underfitting** your data, making it hard for it to have high predictive accuracy and for you to generalize your knowledge from the training set to the test set.

A high **variance** error is due to **too much complexity in the learning algorithm you’re using**. This leads to the algorithm being highly sensitive to high degrees of variation in your training data, which can lead your model to **overfit** the data. You’ll be carrying **too much noise** from your training data for your model to be very useful for your test data.

![](<../../.gitbook/assets/image (16).png>)

<table data-header-hidden><thead><tr><th></th><th width="118.18359375"></th><th width="121.85546875"></th><th></th></tr></thead><tbody><tr><td><strong>Model Type</strong></td><td><strong>Bias</strong></td><td><strong>Variance</strong></td><td><strong>Characteristics</strong></td></tr><tr><td>Linear Regresion</td><td>High</td><td>Low</td><td>Very stiff model, doesn't capure non-linear relations. Easy to interpret.</td></tr><tr><td>Deep Decisision Tree</td><td>Low</td><td>High</td><td>It adjusts too much to the training set. Overfitting.</td></tr><tr><td>Shallow Tree</td><td>Moderate</td><td>Moderate</td><td>Better balance but less stregth.</td></tr><tr><td>Random Forest (many trees)</td><td>Low</td><td>Low</td><td>Reduces variance by averaging trees. Generalizes well.</td></tr><tr><td>KNN with k=1</td><td>Low</td><td>Very high</td><td>Totally depending on training data. Very sensitive.</td></tr><tr><td>Neural Network (tiny with few layers)</td><td>High</td><td>Low</td><td>Cannot learn too complex relationships</td></tr><tr><td>Big non-regularized Neural Network</td><td>Low</td><td>High</td><td>High tendency to overfitting.</td></tr></tbody></table>

{% hint style="success" %}
Too Simple Models [![U+21E8.gif](https://upload.wikimedia.org/wikipedia/commons/6/61/U%2B21E8.gif)](https://en.wikipedia.org/wiki/File:U%2B21E8.gif)Bias Error

Too Complex Models[![U+21E8.gif](https://upload.wikimedia.org/wikipedia/commons/6/61/U%2B21E8.gif)](https://en.wikipedia.org/wiki/File:U%2B21E8.gif)Variance Error
{% endhint %}

### Error decomposition

The **bias-variance decomposition** essentially **decomposes the learning error** from any algorithm by adding the **bias**, the **variance**, and **a bit of irreducible error due to noise in the underlying dataset**. Essentially, if you make the model more complex and add more variables, you’ll lose bias but gain some variance — in order to get the optimally reduced amount of error, you’ll have to tradeoff bias and variance. You don’t want either high bias or high variance in your model.

{% hint style="info" %}
_total\_error = bias\_error² + variance\_error + irreducible\_error_
{% endhint %}

![](<../../.gitbook/assets/image (102).png>)

### How can we overcome it?

> If our model complexity exceeds this sweet spot, we are in effect over-fitting our model; while if our complexity falls short of the sweet spot, we are under-fitting the model. In practice, **there is not an analytical way to find this location**. Instead we **must use an accurate measure of prediction error** and explore differing levels of model complexity and then choose the complexity level that minimizes the overall error. A key to this process is the selection of an _accurate_ error measure as often grossly inaccurate measures are used which can be deceptive.
>
> _Scott Fortmann-Roe -_ [_Understanding the Bias-Variance tradeoff_](http://scott.fortmann-roe.com/docs/BiasVariance.html)

Some ways to achieve the Bias-Variance Tradeoff:

* [**Regularizacion**](../ml-techniques/regularization.md) techniques (L1 or L2)
* A good option would be **applying** [**cross-validation**](../ml-techniques/cross-validation.md)**.**
* Using [**ensemble methods**](../ml-techniques/ensemble-methods.md) like bagging and **Resampling** techniques
  * One modeling algorithm that makes use of bagging is **Random Forests**. Here, the bias of the full model is equivalent to the bias of a single decision tree–which itself has high variance. By creating many of these trees, in effect a “forest”, and then averaging them the variance of the final model can be greatly reduced over that of a single tree.
  * For further details, check [ensemble methods](../ml-techniques/ensemble-methods.md).

{% hint style="info" %}
Additional marks:

* Generally, **resampling-based measures** such as **cross-validation** should help. Generally, resampling-based measures such as cross-validation should be **preferred over theoretical measures such as Aikake's Information Criteria**.
  * Akaike’s information criterion ([AIC](https://www.statisticshowto.com/akaikes-information-criterion/)) compares the quality of a set of statistical models to each other. For example, you might be interested in what variables contribute to low socioeconomic status and how each variable contributes to that status. Let’s say you create several [regression ](https://www.statisticshowto.com/probability-and-statistics/regression-analysis/)models for various factors like education, family size, or disability status; the AIC will take each model and rank them from best to worst. The “best” model will be the one that neither under-fits nor over-fits.
* **Adjusting minor parameters** in some estimators:
  * Both the **k-nearest** and Support Vector Machines(**SVM**) algorithms have **low bias and high variance**. But the trade-offs in both these cases can be changed:
    * In the K-nearest algorithm, the value of k can be increased, which would simultaneously increase the number of neighbors that contribute to the prediction. This in turn would increase the bias of the model.&#x20;
    * Whereas, in the SVM algorithm, the trade-off can be changed by an increase in the C parameter that would influence the violations of the margin allowed in the training data. This will increase the bias but decrease the variance.
{% endhint %}
