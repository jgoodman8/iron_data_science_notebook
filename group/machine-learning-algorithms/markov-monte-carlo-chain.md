# Markov Monte Carlo Chain

{% hint style="info" %}
_Sources:_ 

* [_Chapter 3: Probabilistic Programming and Bayesian Methods for Hackers_](https://github.com/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/tree/master/Chapter3_MCMC)
{% endhint %}

## The landscape

Given a Bayesian inference problem with $$N$$ unknowns, we are creating an _N-dimensional_ space for the _prior distributions_ to exist in. We may describe this space or additional space as the _**surface**_ that reflects the _prior probability_  on a particular point.

![Given p1, p2 ~ Uni\(0, 5\), the space created is a square and the surface is a fat plane at the top of it](../../.gitbook/assets/image%20%2817%29.png)

What happens to our space after we incorporate our observed data$$X$$? The data $$X$$ does not change the space, but it changes the surface of the space by _pulling and stretching the fabric of the prior surface_ to reflect where the true parameters likely live. More data means more pulling and stretching, and our original shape becomes mangled or insignificant compared to the newly formed shape. Less data, and our original shape is more present. Regardless, the resulting surface describes the _posterior distribution_.

![Prior probability recreated as the surface given p1~Exp\(3\), p2~Exp\(10\)](../../.gitbook/assets/image%20%2846%29.png)

Notice that the posterior landscapes look different from one another, though the data observed is identical in both cases. The reason is as follows: the exponential-prior landscape puts very little _posterior_ weight on values in the upper right corner of the figure; this is because _the prior does not put much weight there_. On the other hand, the uniform-prior landscape is happy to put posterior weight in the upper-right corner, as the prior puts more weight there.

![Landscape for both distributions given an observation](../../.gitbook/assets/image%20%2834%29.png)

The black dot represents the true parameters. Even with 1 sample point, **the mountains attempts to contain the true parameter**. Of course, inference with a sample size of one is incredibly naive, and choosing such a small sample size was only illustrative.

## The MCMC landscape

Through this approach we may **find out the posterior mountains** \(and therefore the "best" parameters\). However, we cannot naively search over a _N-dimensional_ space, due to becomes a $$O(exp(N))$$ problem.  So, the idea behind MCMC is to **perform an intelligent and efficient search of the space**.

MCMC returns _samples_ from the posterior distribution, not the distribution itself. It performs a task similar to repeatedly asking "How likely is this point I found to be from the mountain I am searching for?", and completes its task by returning thousands of accepted points in hopes of reconstructing the original mountain.

### The MCMC algorithm

There is a large family of algorithms that perform MCMC. However, they may be expressed as follows:

1. Start at **current position**
2. Propose moving to a new position $$\Rightarrow$$ **Explore closer points**
3. **Evaluate new point** based on the position's adherence to the data and prior distributions
   1. If accept: **move to the new position**. Return to Step 1
   2. If reject: **don't move**. Return to Step 1
4. After a large number of iterations, **return all accepted positions**.

This way we move in the general direction towards the regions where the posterior distributions exist, and collect samples sparingly on the journey. If the current position of the MCMC algorithm is in an area of extremely low probability, which is often the case when the algorithm begins, **the algorithm will move in positions** _**that are likely not from the posterior**_ **but better than everything else nearby**. Thus the first moves of the algorithm are not reflective of the posterior distribution.

 Inference using **the first few thousand points** is a bad idea, as they are unrelated to the final distribution we are interested in. Thus is it a good idea to **discard** those samples before using the samples for inference. We call this period before converge **the** _**burn-in period**_.

#### Alternatives to MCMC

There are other procedures for determining the posterior distributions:

* [Laplace approximation](https://en.wikipedia.org/wiki/Laplace%27s_method)
* [Variational Bayes](https://en.wikipedia.org/wiki/Variational_Bayesian_methods)

### Prediction step

A naive method to compute this is to **re-run the above MCMC with the additional data point appended**. The disadvantage with this method is that it will be **slow** to infer for each novel data point. Alternatively, we can try a _less precise_, but much quicker method. We will use **Bayes Theorem** for this, given the found parameters for our posterior distribution.

### About convergence

#### Autocorrelation

By the nature of the MCMC algorithm, we will always be returned samples that exhibit autocorrelation \(this is because of the step `from your current position, move to a position near you`\). A chain that is **not exploring the space well** will exhibit very **high autocorrelation**. Visually, if the trace seems to meander like a river, and not settle down, the chain will have high autocorrelation. This does **not imply that a converged MCMC has low autocorrelation**. Hence low autocorrelation is not necessary for convergence, but it is sufficient.

#### Thinning

If there is high-autocorrelation between posterior samples. Many post-processing algorithms require samples to be _independent_ of each other. This can be solved, or at least reduced, by only returning to the user every _n-th_ sample, thus removing some autocorrelation. **With more thinning, the autocorrelation drops quicker**. There is a tradeoff though: **higher thinning requires more MCMC iterations** to achieve the same number of returned samples.

![](../../.gitbook/assets/image%20%282%29.png)

#### Intelligence starting values

It would be great to start the MCMC algorithm off near the posterior distribution, so that it will take little time to start sampling correctly. We can aid the algorithm by telling where we "think" the posterior distribution will be by **specifying the** _**testval**_ **parameter in the** _**Stochastic**_ **variable creation**. In many cases we can produce a reasonable guess for the parameter.

```text
mu = tfd.Uniform(name="mu", low=0., high=100.).sample(seed=data.mean())
```

#### What if it does not converge?

If the **priors are poorly chosen**, the MCMC algorithm **may not converge**, or at least have difficulty converging. Consider what may happen if the prior chosen **does not even contain the true parameter**.

{% hint style="warning" %}
_If prior probability = 0_ $$\Rightarrow$$ _Posterior  probability = 0_
{% endhint %}

