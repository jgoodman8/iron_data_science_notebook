# Distributions

{% hint style="info" %}
\_\_[_More info about probability distributions \(Statistics How To\)_](https://www.statisticshowto.datasciencecentral.com/probability-distribution/)\_\_
{% endhint %}

## Continuous distributions

### Uniform

A uniform distribution, also called a **rectangular distribution**, is a probability distribution that has **constant probability**.

![](../../.gitbook/assets/image%20%2813%29.png)

This distribution is defined by **two parameters**: minimum $$a$$ and maximum $$b$$. So, for a random variable $$Z \sim Uniform(a, b)$$. And the expected value will be: $$E(X) = \frac{a+b}{2}$$.

### Normal

![](../../.gitbook/assets/image%20%2812%29.png)

A normal distribution, sometimes called the bell curve, is a distribution that occurs naturally in many situations. It is expressed as $$Z \sim Norm(\mu, \sigma²)$$ It has some properties:

* The [mean, mode and median](https://www.statisticshowto.datasciencecentral.com/probability-and-statistics/statistics-definitions/mean-median-mode/) are all equal.
* The curve is symmetric at the center \(i.e. around the mean, μ\).
* Exactly half of the values are to the left of center and exactly half the values are to the right.
* The total area under the curve is 1.

### Lognormal

A lognormal \(or Galton\) distribution is a probability distribution with a normally distributed logarithm. [Skewed distributions](https://www.statisticshowto.datasciencecentral.com/probability-and-statistics/skewed-distribution/) with low mean values, large variance, and all-positive values often fit this type of distribution. Values must be positive as $$log(x)$$ exists only for positive values of $$x$$.

![](../../.gitbook/assets/image%20%2824%29.png)

### Bivariate Normal

A bivariate normal distribution is made up of **two independent random variables**. The two variables in a bivariate normal are **both are normally distributed**, and they have a normal distribution when both are added together.

![](../../.gitbook/assets/bivariate41.gif)

### Exponential

The exponential distribution \(also called the negative exponential distribution\) is a probability distribution that **describes time between events in a Poisson process**. 

The exponential distribution is mostly used for testing [product reliability](http://www.ni.com/white-paper/14412/en/). It’s also an important distribution for building continuous-time [Markov chains](https://www.statisticshowto.datasciencecentral.com/markov-chain-monte-carlo/). The exponential often **models waiting times** and can help you to answer questions like: “How much time will go by before a major hurricane hits the Atlantic Seaboard?”

![](../../.gitbook/assets/image%20%281%29.png)

The most common form of its probability distribution function is:

$$
f_Z(z|λ)=λe^{−λz},z\ge0
$$

When a random variable $$Z$$ has an exponential distribution with parameter $$\lambda$$, we say $$Z$$ is exponential and write $$Z∼Exp(\lambda)$$. Given a specific $$\lambda$$, the expected value of an exponential random variable is equal to the inverse of $$\lambda$$, this is $$E[Z|\lambda] = \frac{1}{\lambda}$$.

## Discrete distributions

### Binomial

![](../../.gitbook/assets/image%20%2841%29.png)

The binomial distribution gives the **discrete probability distribution** $$P_p(n|N)$$ of **obtaining exactly** $$n$$ **successes out of** $$N$$ **Bernoulli trials**. The binomial distribution is therefore given by:

$$
𝑃(𝑋=𝑘)= {{N}\choose{k}}  𝑝^𝑘(1−𝑝)^{𝑁−𝑘}
$$

If $$X$$ is a binomial random variable with parameters $$p$$ and $$N$$, denoted $$X \sim \text{Bin}(N,p)$$, then $$X$$ is the number of events that occurred in the $$N$$ trials \(obviously $$0 \le X \le N$$\). The larger $$p$$ is \(while still remaining between 0 and 1\), the more events are likely to occur. The expected value of a binomial is equal to $$Np$$.

### Bernoulli

![](../../.gitbook/assets/image%20%2846%29.png)

A Bernouilli distribution is a discrete probability distribution for a Bernouilli trial — a random experiment that has only two outcomes \(usually called a “Success” or a “Failure”\). For example, the probability of getting a heads \(a “success”\) while flipping a coin is 0.5. The probability of “failure” is 1 – P \(1 minus the probability of success, which also equals 0.5 for a coin toss\). It is a special case of the binomial distribution for n = 1. In other words, it is a binomial distribution with a single trial \(e.g. a single coin toss\). 

The [probability density function \(pdf\)](https://www.statisticshowto.datasciencecentral.com/probability-density-function/) for this distribution is $$p^x (1 – p)^{1 – x}$$, which can also be written as:

$$
P(n) = \begin{cases} 1-p, & \text{if}\ n=0 \\ p, & \text{if}\ n=1 \end {cases}
$$

If a random variable $$Z$$ has a **mass distribution**, we denote this by writing $$X \sim \text{Bernouilli}(p)$$. The[ expected value](https://www.statisticshowto.datasciencecentral.com/probability-and-statistics/expected-value/) for a random variable, X, from a Bernoulli distribution is $$E[X] = p$$.

### Poisson

![](../../.gitbook/assets/image%20%288%29.png)

A Poisson distribution is a tool that helps to predict the probability of certain events from happening when you know how often the event has occurred. It gives us the **probability of a given number of events happening in a fixed interval of time**. The Poisson distribution is given by:

$$
P(Z=k) = \frac{\lambda^k e^{-\lambda}}{k!}, k = 0,1,2...
$$

If a random variable $$Z$$ has a **mass distribution**, we denote this by writing $$Z \sim \text{Poi}(\lambda)$$. And its expected value is equal to its parameter $$E[ Z|\lambda] = \lambda$$.

