# Covariance vs Correlation Matrix

{% hint style="info" %}
_Sources:_

* \_\_[_Baffled by Covariance and Correlation??? Get the Math and the Application in Analytics for both the terms..._](https://towardsdatascience.com/let-us-understand-the-correlation-matrix-and-covariance-matrix-d42e6b643c22) __[_\(Srishti Saha\)_](https://towardsdatascience.com/@srishtisaha?source=post_page-----d42e6b643c22----------------------)\_\_
* \_\_[_Understanding the Covariance Matrix \(Data Science Plus\)_](https://datascienceplus.com/understanding-the-covariance-matrix/)\_\_
{% endhint %}

## Overview

* _**Covariance**_ $$\Rightarrow$$ **direction** of the linear relationship between variables.
* _**Correlation**_ $$\Rightarrow$$ measure of the **strength and direction** of linear relationship.

> **Correlation values are standardized** whereas, covariance values are not.

## Covariance Matrix

{% hint style="info" %}
Check [covariance definition](../statistics/mean-vs-median.md#covariance).
{% endhint %}

Focusing on the two-dimensional case, the covariance matrix for two dimensions \(or $$x$$ and $$y$$variables\) is given by:

$$
C = 
\begin{pmatrix} 
  \sigma(x,x)  & \sigma(x,y) \\ 
  \sigma(y,x) & \sigma(y,y) 
\end{pmatrix}
$$

{% tabs %}
{% tab title="Sample with Numpy" %}
```python
import numpy as np
import matplotlib.pyplot as plt

plt.style.use('ggplot')
plt.rcParams['figure.figsize'] = (12, 8)

mean = 0
std = 1
num_samples = 500

x = np.random.normal(mean, std, num_samples)
y = np.random.normal(mean, std, num_samples)
X = np.vstack((x, y)).T  # Join both arrays and transpose
# X = np.stack(arrays=[x, y], axis=1) # Equivalent transformation

plt.scatter(X[:, 0], X[:, 1])
plt.title('Generated Data')
plt.axis('equal');
```

![](../../.gitbook/assets/image%20%2877%29.png)
{% endtab %}

{% tab title="Sample with Tensorflow Probability" %}
```python
import tensorflow_probability as tfp
import matplotlib.pyplot as plt

tfd = tfp.distributions
data = tfd.MultivariateNormalFullCovariance(
      loc = [0., 5], # Mean for each variable ==> mean(a) = 0, mean(b) = 5
      covariance_matrix = [[1., .7], [.7, 1.]] # Covariance matrix
).sample(1000)

plt.scatter(data[:, 0], data[:, 1], color='blue', alpha=0.4)
plt.axis([-5, 5, 0, 10])
plt.title('Data set')
plt.show();
```

![](../../.gitbook/assets/image%20%2850%29.png)
{% endtab %}
{% endtabs %}

## Correlation Matrix

Unlike covariance, the correlation has an upper and lower cap on a range $$[-1, 1]$$.

Correlation coefficient of two variables may be  by dividing the covariance of these variables by the product of the standard deviations of the same values.

$$
\rho_{x,y} = corr(x,y) = \frac{\sigma_{x,y}}{\sigma_{x}^2\sigma_{y}^2}
$$

```python
import pandas as pd

data = np.random.RandomState(seed=0)
correlation = pd.DataFrame(data.rand(10, 10)).corr()

correlation.style.background_gradient(cmap='coolwarm')
```

![](../../.gitbook/assets/image%20%2881%29.png)



