# Optimization

## About optimization

Given _W_ the weights matrix, we need to find out the best solution that minimizes the loss function and optimizes the success metric or metrics.

### Random search

Randomly checking N random weight matrixes and selecting the one that behaves the best in the training set.

### Follow the slope

$$
slope\_in\_one\_dimension= \frac{df(x)}{dx} = \lim_{h\to0} \frac{f(x + h) - f(x)}{h}
$$



In multiple dimensions, the **gradient** is the vector of partial derivatives along each dimension. The slope in any direction is the **dot product** of the direction with the gradient. The direction of the **steepest descent is the negative gradient**.

In practice, we will follow the analytic gradient (Newton-Raphson method).

{% embed url="https://www.youtube.com/watch?v=f9wIElV4s0A" %}

## Gradient descent

### Vanilla Gradient Descent (GD)

```python
weights = np.random(N)

while True:
  weights_grad = evaluate_gradient(loss_fun, data, weights)  # current gradient
  weights += - step_size * weights_grad  # parameter update
```

_Step size_ updates the weights in the opposite direction to the gradient. Since the gradient points to the direction of the greatest increase of the function `- step_size` helps us to slowly move in the direction of the greatest decrease. This variable is a hyperparameter of the algorithm, also called the **learning rate**.

{% content-ref url="hyperparameter-tuning.md" %}
[hyperparameter-tuning.md](hyperparameter-tuning.md)
{% endcontent-ref %}

We want the Slope to be closer to 0, to minimize it. To compute the partial derivative of the loss w.r.t. $$w_1$$, we can apply the chain rule:

<figure><img src="../../.gitbook/assets/image (3).png" alt="" width="420"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

To go more in detail about how GD works, we can observe this pseudo code:

```python
from ai_framework import activation_fn  # output of the model

n = 1000  # number of data samples
epochs = 10  # number of iterations across all the dataset
alpha = 0.2  # learning rate
weight1 = 0  # model weigth
bias = 0  # model bias

for _ in range(epochs):
    overall_loss = 0
    for x, y in range(n):
        z = pred(weight1, bias, x)
        output = activation(z)
        overall_loss += loss_fn(output, y)
    overall_loss /= n    
    derivative_weight1, derivative_bias = compute_partial_derivatives(overall_loss)
    weight1 -= alpha * derivative_weight1
    bias -= alpha * derivative_bias
```

### Stochastic Gradient Descent

{% hint style="info" %}
Source:&#x20;

* [Deep Learning Part 2: Vanilla vs Stochastic Gradient Descent](https://medium.com/geekculture/deep-learning-part-2-vanilla-vs-stochastic-gradient-descent-6bcecc26fd51)
{% endhint %}

In stochastic gradient descent, rather than calculating the error as an average of **all** the training examples, we select _M random training examples_ from the entire dataset and use that in our cost function. We call this subset a **mini-batch**.

Once our network has been trained on all the data points in our mini-batch, we select a new subset of random points and train our model with that. We continue this process until we’ve exhausted all training points, at which point we’ve completed an **epoch**. We then start with a new **epoch** and continue until convergence.

{% hint style="success" %}
Main differences w.r.t. the "standard" Gradient Descent:

* Partial derivates are computed on every training sample
* Meaning, model weights, and bias are updated after each sample
* The step size (alpha) is smaller to avoid big changes between samples
{% endhint %}

{% hint style="info" %}
There's a variant called **Minibatch GD:**

* Mini batches are used (with $$2^x$$ sizes)
* Parameters are updated after each mini-batch
* This solution is **less noisy** than SGD
* But converges **faster** than Vanilla GD
* Better GPU usage
{% endhint %}

### GD with momentum

TBA

### Adam optimizer

TBA
