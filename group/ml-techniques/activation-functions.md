# Activation Functions

{% hint style="info" %}
_Sources:_

* \_\_[_Understanding Categorical Cross-Entropy Loss, Binary Cross-Entropy Loss, Softmax Loss, Logistic Loss, Focal Loss and all those confusing names \(Raúl Gómez blog\)_](https://gombru.github.io/2018/05/23/cross_entropy_loss/)
{% endhint %}

## Sigmoid

It transforms a vector in the continuous range \[0, 1\]. It's also called **logistic function**.

![](../../.gitbook/assets/image%20%2888%29.png)

{% tabs %}
{% tab title="Formula" %}
$$
f(s_i) = \frac{1}{1 + e^{-s_i}}
$$
{% endtab %}

{% tab title="Example in tf.keras" %}
A _sigmoid_ activation may be used within a[ Dense Keras Layer](https://www.tensorflow.org/versions/r2.0/api_docs/python/tf/keras/layers/Dense?hl=en):

```python
from tensorflow.keras.layers import Dense
from tensorflow.keras.models import Model

input_layer = # Previous layer

logits = Dense(
    units=32,
    activation='sigmoid'
)(input_layer)

model = Model(inputs=input_layer, outputs=logits)
```
{% endtab %}

{% tab title="Example in tf.math" %}
It provides [support](https://www.tensorflow.org/versions/r2.0/api_docs/python/tf/math/sigmoid?hl=en) to the operation by computing sigmod of _x_ element-wise.

```python
import tensorflow as tf

tf.math.sigmoid(
    x, # A tensor of "floating type"
    name=None # Optional
)
```
{% endtab %}
{% endtabs %}

## Softmax



