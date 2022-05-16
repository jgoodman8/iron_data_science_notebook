# Loss functions

{% hint style="info" %}
_Sources:_

* __[_Understanding Categorical Cross-Entropy Loss, Binary Cross-Entropy Loss, Softmax Loss, Logistic Loss, Focal Loss and all those confusing names (Raúl Gómez blog)_](https://gombru.github.io/2018/05/23/cross\_entropy\_loss/)
* __[_What is loss function? (Christophee Pere_](https://towardsdatascience.com/what-is-loss-function-1e2605aeb904)_)_
* __[_Machine Learning Glossary_](https://ml-cheatsheet.readthedocs.io/en/latest/index.html)__
{% endhint %}

## What are loss functions?

{% hint style="success" %}
A way to **measure whether the algorithm is doing a good job**.

This is necessary to determine the **distance between the algorithm’s current output** **and its expected output**. The measurement is used as a **feedback signal** to adjust how the algorithm works. This adjustment step is what we call _learning_.&#x20;

_François Chollet, Deep learning with Python (2017), Manning, chapter 1 p.6_
{% endhint %}



It can be categorized into two groups. One for **classification** (discrete values, 0,1,2…) and the other for **regression** (continuous values).

Commonly used loss functions:

* For classification:
  * Cross-entropy
  * Log-Loss
  * Exponential Loss
  * Hinge Loss
  * Kullback Leibler Divergence Loss
* For regression:
  * Mean Square Error Loss  (L2)
  * Mean Absolute Error Loss (L1)
  * Huber Loss

### Cross-entropy

{% hint style="success" %}
Cross-entropy is a **measure of the difference between two probability distributions** for a given random variable or set of events.
{% endhint %}

#### **About entropy and Information Theory**

**Information** quantifies the **number of bits required to encode and transmit an event**. Lower probability events have more information, higher probability events have less information.

In information theory, we like to describe the “_surprise_” of an event. An event is more surprising the less likely it is, meaning it contains more information.

* **Low Probability Event** (_surprising_): More information.
* **Higher Probability Event** (_unsurprising_): Less information.

Information _h(x)_ can be calculated for an event _x_, given the probability of the event _P(x)_ as follows:

$$
h(x) = -log(P(x))
$$

{% hint style="success" %}
**Entropy** is the **number of bits required to transmit a randomly selected event from a probability distribution**.

A _skewed distribution has low entropy_, whereas a distribution where events have _equal probability has a larger entropy_.
{% endhint %}

#### So, what's cross-entropy?

**Cross-entropy** builds upon the idea of entropy from information theory and calculates the number of bits required to represent or transmit an average event from one distribution compared to another distribution.

{% hint style="info" %}
If we consider a target distribution P and an approximation of the target distribution Q, then the _cross-entropy of Q from P is the **number of additional bits** to represent an event **using Q instead of P**_.
{% endhint %}

The result is a value $$[0, \infty)$$:&#x20;

* **0.00**: Perfect probabilities
* **< 0.02**: Great probabilities
* **< 0.20**: Great
* **> 0.30**: Not great
* **> 2.00** Something is not working

In binary classification, where the number of classes $$M$$  equals 2, cross-entropy can be calculated as:

$$
−(ylog(p)+(1−y)log(1−p))−(ylog⁡(p)+(1−y)log⁡(1−p))
$$

If _M>2_ (i.e. multiclass classification), we calculate a separate loss for each class label per observation and sum the result.

$$
−∑c=1Myo,clog(po,c)
$$

### ​Log-Loss

The Log-Loss is the Binary cross-entropy up to a factor 1 / log(2). This loss function is convex and grows linearly for negative values: this means it's less sensitive to outliers. The common algorithm which uses the Log-loss is the _**logistic regression**_.

{% content-ref url="../machine-learning-algorithms/supervised-learning/logistic-regression.md" %}
[logistic-regression.md](../machine-learning-algorithms/supervised-learning/logistic-regression.md)
{% endcontent-ref %}

### Exponential Loss

The exponential loss is convex and grows exponentially for negative values which makes it more sensitive to outliers. The exponential loss is used in the [AdaBoost algorithm](https://en.wikipedia.org/wiki/AdaBoost).

$$
exp\_loss = 1/m * sum(exp(-y*f(x)))
$$

![](<../../.gitbook/assets/image (125).png>)

{% content-ref url="../machine-learning-algorithms/supervised-learning/adaptative-boosting.md" %}
[adaptative-boosting.md](../machine-learning-algorithms/supervised-learning/adaptative-boosting.md)
{% endcontent-ref %}

### Hinge Loss

It's a loss function used for “maximum-margin” classification, most notably for support vector machines (SVM).

$$
Hinge = max(0, 1-y*f(x))
$$

![](<../../.gitbook/assets/image (123).png>)

{% content-ref url="../machine-learning-algorithms/supervised-learning/support-vector-machines.md" %}
[support-vector-machines.md](../machine-learning-algorithms/supervised-learning/support-vector-machines.md)
{% endcontent-ref %}

### MSE Loss (L2 regularization)

The square difference between the current output _y\_pred_ and the expected output _y\_true_ divided by the number of outputs.

**It's very sensitive to outliers** because the difference is a _square that gives more importance to outliers_.

![](<../../.gitbook/assets/image (118).png>)

{% hint style="info" %}
The behavior is a quadratic curve especially **useful for gradient descent algorithms**. The gradient will be smaller close to the minima. MSE is very useful **if outliers are importan**t for the problem, **if outliers are noisy** or bad data or bad measures you should use the MAE loss function.
{% endhint %}

{% content-ref url="regularization.md" %}
[regularization.md](regularization.md)
{% endcontent-ref %}

### MAE Loss (L1 regularization)

At the difference of the previous loss function, the square is replaced by an absolute value. This difference has a big impact on the behavior of the loss function which has a “V” form.&#x20;

{% hint style="info" %}
The **MAE function is more robust to outliers** because it is based on absolute value compared to the square of the MSE. It’s like a median, outliers can’t really impact her behavior.
{% endhint %}

![](<../../.gitbook/assets/image (121).png>)

{% content-ref url="regularization.md" %}
[regularization.md](regularization.md)
{% endcontent-ref %}

### Huber Loss

It is **a combination of MAE and MSE** (L1-L2) but it _depends on an additional parameter called delta_ that influences the shape of the loss function. This parameter needs to be fine-tuned by the algorithm. **When the values are large (far from the minima), the function has the behavior of the MAE, and closer to the minima, the function behaves like the MSE**. So the _**delta**_ parameter is your sensitivity to outliers.

![](<../../.gitbook/assets/image (122).png>)
