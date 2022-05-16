# Optimization

Given _W_ the weights matrix, we need to find out the best solution that minimizes the loss function and optimizes the success metric or metrics.

## About optimization

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

### Vanilla GD

```python
weights = np.random(N)

while True:
  weights_grad = evaluate_gradient(loss_fun, data, weights)  # current gradient
  weights += - step_size * weights_grad  # parameter update
```

_Step size_ updates the weights in the opposite direction to the gradient. Since the gradient points to the direction of the greatest increase of the function, `- step_size` helps us to slowly move in the direction of the greatest decrease. This variable is a hyperparameter of the algorithm, also called the **learning rate**.

{% content-ref url="hyperparameter-tuning.md" %}
[hyperparameter-tuning.md](hyperparameter-tuning.md)
{% endcontent-ref %}

### Stochastic GD

### GD with momentum

TBA

### Adam optimizer

TBA
