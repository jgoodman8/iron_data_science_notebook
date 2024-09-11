# The bayesian basis

{% hint style="info" %}
[_Chapter 1 - Probabilistic Programming and Bayesian Methods for Hackers_](https://nbviewer.jupyter.org/github/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/blob/master/Chapter1\_Introduction/Ch1\_Introduction\_TFP.ipynb#Probability-Distributions)
{% endhint %}

## Bayesian vs Frequentist

**Frequentist** (the more classical version of statistics) assume that **probability is the long-run frequency of events**. This makes logical sense for many probabilities of events, but becomes more difficult to understand when events have no long-term frequency of occurrences.

**Bayesians** interpret a probability as **measure of belief**, or confidence, of an event occurring. Simply, a probability is a summary of an opinion.

## So what?

* The belief about event _A_ is denoted as _P(A)_. We call this quantity the **prior probability**.
* Given a **new evidence **_**X**_, it cannot be ignored. Even if the evidence is counter to what was initially believed, the evidence.
* We denote our updated belief as _P(A|X)_, interpreted as the probability of A given the evidence X. We call the updated belief the **posterior probability** so as to contrast it with the prior probability.

### Bayes' Theorem

$$
P(A|X) = \frac{P(X|A) \cdot P(A)}{P(X)}
$$

## Probability distributions

Let Z be some random variable. It may be discrete, continuous or mixed.

### Discrete variables

The distribution of this random variable Z will be a _**probability mass function**_ or **pmf**. Let's say a random variable Z is _Poisson-distributed,_ $$\lambda$$ would be the **parameter of the distribution**. So, it controls the distribution's shape.

$$
P(Z=k) = \frac{\lambda^k e^{-\lambda}}{k!}, k = 0,1,2...
$$

Then, the probability mass distribution of the random variable Z will be denoted by writing $$Z∼Poi(λ)$$.

![](<../../.gitbook/assets/image (22) (1).png>)

### Continuous variables

A  continuous random variable has a _**probability density function**_. An example of continuous random variable is a random variable with _exponential density_.

$$
f_Z(z|λ)=λe^{−λz},z\ge0
$$

When a random variable Z has an exponential distribution with parameter $$\lambda$$, we say Z is exponential and write $$Z∼Exp(λ)$$.

![](<../../.gitbook/assets/image (54).png>)

### How do we find λ?

In the real world, λ is hidden from us. We see only Z, and must go backwards to try and determine λ. **Bayesian inference** is concerned with _beliefs_ about what λ might be. Rather than try to guess λ exactly, we can only talk about what λ is likely to be by assigning a probability distribution to λ.

