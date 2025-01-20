# Feature Normalization

## 0 - 1 Normalization

$$
x_j^{[i]} = \frac{x_j^{[i]} - min(x_j) }{max(x_j) - min(x_j)}
$$

## Z-score Normalization

{% hint style="success" %}
More recommended when using DL methods (due to the zero-centering)
{% endhint %}

$$
x_j^{[i]} = \frac{x_j^{[i]} - mean(x_j) }{std(x_j)}
$$
