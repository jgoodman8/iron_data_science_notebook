# Z-score

Also known as _standard score of an observation_, this method assumes data follows a gaussian distribution.

{% hint style="danger" %}
It's a parametric method which indicates **how many standard deviations** an instance is **from the sample’s mean**.
{% endhint %}

![](../../.gitbook/assets/image%20%2833%29.png)

The z-score of every data point is calculated using the formula: $$z = (x-\mu)/\sigma$$. It can be easily calculated using the method provided by [sklearn](https://docs.scipy.org/doc/scipy-0.17.0/reference/generated/scipy.stats.zscore.html).

Once every z-score is computed, **outliers are detected given a threshold**. It's usually set to: $$2.5$$, $$3.0$$ or $$3.5$$.

