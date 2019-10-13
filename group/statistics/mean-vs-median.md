# The basics

![](../../.gitbook/assets/image%20%2875%29.png)

{% hint style="info" %}
_Credits & Sources:_

* \_\_[_What would be some examples of when the "mean" would be preferred over the "median"?_](https://www.quora.com/What-would-be-some-examples-of-when-the-mean-would-be-preferred-over-the-median)\_\_
* \_\_[_Mean, Median, Mode: What They Are, How to Find Them \(Statistics How To\)_](https://www.statisticshowto.datasciencecentral.com/probability-and-statistics/statistics-definitions/mean-median-mode/)\_\_
* \_\_[_Mean \(Wikipedia\)_](https://en.wikipedia.org/wiki/Mean)\_\_
* \_\_[_Median \(Wikipedia\)_](https://en.wikipedia.org/wiki/Median)
* \_\_[_Range \(Wikipedia\)_](https://en.wikipedia.org/wiki/Range)\_\_
* \_\_[_Mode \(Wikipedia\)_](https://en.wikipedia.org/wiki/Mode_%28statistics%29)
* \_\_[_Variance \(Wikipedia\)_](https://en.wikipedia.org/wiki/Variance)\_\_
* \_\_[_Standard deviation \(Wikipedia\)_](https://en.wikipedia.org/wiki/Standard_deviation)\_\_
* \_\_[_Standard eror \(Wikipedia\)_](https://en.wikipedia.org/wiki/Standard_error)\_\_
* \_\_[_Statistical mean, median, mode and range \(Margaret Rouse, Tech Target\)_](https://searchdatacenter.techtarget.com/definition/statistical-mean-median-mode-and-range)\_\_
* \_\_[_Mean vs. Median: When to Use? \(Stack Exchange\)_](https://math.stackexchange.com/questions/2304710/mean-vs-median-when-to-use)
* \_\_[_Standard deviation and Variance \(Math is Fun\)_](https://www.mathsisfun.com/data/standard-deviation.html)\_\_
* \_\_[_Understanding Principal Components Analysis \(Rishav Kumar\)_](https://medium.com/@aptrishu/understanding-principle-component-analysis-e32be0253ef0)\_\_
{% endhint %}

## Properties of distributions

### Mean

{% tabs %}
{% tab title="Discrete distribution" %}
Found by **adding all of the numbers** together **and dividing by the number of items** in the set:

$$
{\bar {x}}={\frac {1}{n}}\left(\sum _{i=1}^{n}{x_{i}}\right)={\frac {x_{1}+x_{2}+\cdots +x_{n}}{n}}
$$
{% endtab %}

{% tab title="Continuous distribution" %}
It's obtained by integrating the product of the variable with its probability as defined by the distribution. Given the $$f(x)$$ continuous [probability distribution](the-bayesian-basis.md#probability-distributions):

$$
\mu = \int _{-\infty }^{\infty }xf(x)\,dx
$$
{% endtab %}

{% tab title="Types" %}
* \*\*\*\*[**Geometric mean**](https://en.wikipedia.org/wiki/Geometric_mean)\*\*\*\*
* \*\*\*\*[**Harmonic mean**](https://en.wikipedia.org/wiki/Harmonic_mean)\*\*\*\*
* **...**
{% endtab %}
{% endtabs %}

### Median

{% tabs %}
{% tab title="Discrete distribution" %}
It depends on whether the number of terms in the distribution. Once the values are sorted.

* If the given number of terms is **odd**:
  * It's **the value in de middle**.
  * 1, 3, 3, **6**, 7, 8, 9 $$\Rightarrow$$ **6**
* If the given number of terms is **even**:
  * It's the **average of the two terms in the middle**.
  * 1, 2, 3, **4**, **5**, 6, 8, 9 $$\Rightarrow$$\(4+5\) $$\div$$ 2 = **4.5**
{% endtab %}

{% tab title="Continuos distribution" %}
It's the value _m_ such that the **probability is at least 0.5** that a **randomly chosen poin**t on the function will be **less than or equal to** _**m**_.

$$
\operatorname {P} (X\geq m)=\operatorname {P} (X\leq m)=\int _{-\infty }^{m}f(x)\,dx={\frac {1}{2}}
$$

![](../../.gitbook/assets/image%20%2855%29.png)
{% endtab %}
{% endtabs %}

### Mode

{% tabs %}
{% tab title="Discrete distribution" %}
It's the **most repeated value** within the distribution. Example:

* 1, **2**, **2**, 3, 4, 7, 9 $$\Rightarrow$$ **2**

It's quite common to find **more than one mode**, especially if there aren't many terms. A distribution with two modes is called **bimodal**. As well, with three it's called **trimodal**.
{% endtab %}

{% tab title="Continuous distribution" %}
It's the **maximum value** of the function. As with discrete distributions, there may be more than one mode.

![](../../.gitbook/assets/image%20%285%29.png)
{% endtab %}
{% endtabs %}

### Range

{% tabs %}
{% tab title="Discrete distribution" %}
It's the **difference** between the **maximum** value and the **minimum** value. Example:

* **1**, 2, 2, 3, 4, 7, **9** $$\Rightarrow$$ 9 - 1 = 8
{% endtab %}

{% tab title="Continuous distribution" %}
It's the **difference between the two extreme points on the distribution curve**. For any value outside the range of a distribution, the value of the function is equal to 0.

![Source: Siyavula](../../.gitbook/assets/image%20%2836%29.png)
{% endtab %}
{% endtabs %}

### Variance

It measures how far a set of random numbers are spread out from their [mean](mean-vs-median.md#mean). 

{% tabs %}
{% tab title="Population Variance" %}
$$
\sigma^2 = \frac {1}{N} \sum _{i=1}^{N} (x_{i} - \mu)^2
$$
{% endtab %}

{% tab title="Sample Variance" %}
When data is a sample, this formula is used as a "correction" over the original one.

$$
s^2 = \frac {1}{N-1}\sum _{i=1}^{N}(x_{i}-{\bar {x}})^{2}
$$
{% endtab %}

{% tab title="Example Numpy" %}
```python
import numpy as np

np.random.seed(333)
np.std(np.random.rand(100))
```
{% endtab %}
{% endtabs %}

### Standard deviation

It's is the **squarred root of the** [**variance**](mean-vs-median.md#variance). A low standard deviation indicates that the data points tend to be close to the [mean](mean-vs-median.md#mean).

{% tabs %}
{% tab title="Population Std" %}
$$
\sigma = \sqrt{ \frac {1}{N} \sum _{i=1}^{N} (x_{i} - \mu)^2}
$$
{% endtab %}

{% tab title="Sample Std" %}
When data is a sample, this formula is used as a "correction" over the original one:

$$
s = {\sqrt {{\frac {1}{N-1}}\sum _{i=1}^{N}(x_{i}-{\bar {x}})^{2}}}
$$
{% endtab %}

{% tab title="Example with Numpy" %}
```python
import numpy as np

np.random.seed(333)
np.var(np.random.rand(100))
```
{% endtab %}
{% endtabs %}

### Covariance

It's a **measure of the joint variability of two random variables**. measures of the extent to which corresponding elements from two sets of ordered data move in the same direction. It measures **how much two variables vary together**. It’s similar to [variance](mean-vs-median.md#variance), but where variance tells you how a _single_ variable varies, **co**variance tells you how **two** variables vary together.

{% tabs %}
{% tab title="Population Covariance" %}
$$
\sigma_{XY} = \frac{
  \sum_{(x,y) \epsilon S} (x - \mu_X) (y - \mu_Y)
}{N}
$$
{% endtab %}

{% tab title="Sample Covariance" %}
$$
cov(x, y) = \frac{
\sum_{i=1}^N (x_i - \overline{x}) (y_i - \overline{y})
}{N - 1}
$$
{% endtab %}
{% endtabs %}

{% page-ref page="../frequent-questions/covariance-vs-correlation-matrix.md" %}

## Related questions

![](../../.gitbook/assets/image%20%2823%29.png)

### Mean vs Median

* **Median** is much **less sensitive to outliers**.
* However, almost all **analytic calculations** on sets of data are **more natural in terms of the mean** than the median.
* The **difference between the median and the mean** is useful to represent **how skewed the data is**.
* The **real use of the median** comes **when the data set may contain extreme outliers**. Then, describing the distribution in terms of quartiles can be more informative than quoting $$\mu$$ and $$\sigma$$.
* For [skewed distributions](https://en.wikipedia.org/wiki/Skewness), the mean is not necessarily the same as the median or the mode. For example, mean income is typically skewed upwards by a small number of people with very large incomes, so that the majority have an income lower than the mean. By contrast, the median income is the level at which half the population is below and half is above. The mode income is the most likely income and favors the larger number of people with lower incomes. **Median** and **mode** are often **more intuitive** measures for such **skewed data**, **BUT many skewed distributions are in fact best described by their mean**, including the [**Exponential**](https://en.wikipedia.org/wiki/Exponential_distribution) and [**Poisson**](https://en.wikipedia.org/wiki/Poisson_distribution) distributions.

![Comparison of mean, median and mode of two log-normal distributions with different skewness.](../../.gitbook/assets/image%20%2812%29.png)

### Difference between standard deviation of a sample and standard error of the population mean

Meanwhile the [standard deviation](mean-vs-median.md#standard-deviation) expresses how disperse is data with respect to the [mean](mean-vs-median.md#mean), the **standard error** meansures the  [standard deviation](https://en.wikipedia.org/wiki/Standard_deviation) of its [sampling distribution](https://en.wikipedia.org/wiki/Sampling_distribution).

The [**sampling distribution**](https://en.wikipedia.org/wiki/Sampling_distribution) of a population mean is **generated by repeated sampling** and recording of the means obtained. This forms a distribution of different means, and this distribution has its own [mean](https://en.wikipedia.org/wiki/Mean) and [variance](https://en.wikipedia.org/wiki/Variance).

{% tabs %}
{% tab title="Standard Error of a Population" %}
Given the standard error of the population $$\sigma$$ and the size $$n$$ of a sample, the standard error of a sample of this population is expressed as:

$$
\sigma_{x}^{-} = \frac{\sigma}{\sqrt{n}}
$$
{% endtab %}

{% tab title="Standard Error of a Sample" %}
 Since the [population standard deviation](https://en.wikipedia.org/wiki/Standard_deviation) is seldom known, the standard deviation of a sample is used to aproximate this statistic:

$$
s{x}^{-} = \frac{s}{\sqrt{n}}
$$
{% endtab %}
{% endtabs %}

