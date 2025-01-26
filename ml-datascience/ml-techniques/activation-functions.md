# Activation Functions

{% hint style="info" %}
_Sources:_

* [_Understanding Categorical Cross-Entropy Loss, Binary Cross-Entropy Loss, Softmax Loss, Logistic Loss, Focal Loss and all those confusing names (Raúl Gómez blog)_](https://gombru.github.io/2018/05/23/cross_entropy_loss/)
{% endhint %}

## Linear

The input equals the output $$f(z)  = z$$. Meaning the output is continuous.

<figure><img src="../../.gitbook/assets/image (128).png" alt=""><figcaption></figcaption></figure>

## Sigmoid or Logistic function

It transforms a vector in the continuous range \[0, 1].

![](<../../.gitbook/assets/image (89).png>)

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

{% hint style="success" %}
Converts its input values into a probability distribution among _N_ classes.
{% endhint %}

Transforms raw scores into probabilities in a multi-label classification. All the p**robabilities are normalized to sum 1** all of them.&#x20;

$$
f(s_i) = \frac{ e^{x_i}}{\sum_j e^{x_j}}
$$

### ReLU

Also called Rectified Linear Unit,

* if the input value is ≥ 0, (acts as a [#linear](activation-functions.md#linear "mention") function)
* it the input value is < 0, it returns 0

{% hint style="success" %}
It can be summarized as $$ReLU(z) = max(0, z)$$
{% endhint %}

<figure><img src="../../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>
