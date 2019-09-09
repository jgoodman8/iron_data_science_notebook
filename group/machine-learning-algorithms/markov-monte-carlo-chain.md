# Markov Monte Carlo Chain

## The landscape

Given a Bayesian inference problem with $$N$$ unknowns, we are creating an _N-dimensional_ space for the _prior distributions_ to exist in. We may describe this space or additional space as the _**surface**_ that reflects the _prior probability_  on a particular point.

![Given p1, p2 ~ Uni\(0, 5\), the space created is a square and the surface is a fat plane at the top of it](../../.gitbook/assets/image%20%289%29.png)

What happens to our space after we incorporate our observed data$$X$$? The data $$X$$ does not change the space, but it changes the surface of the space by _pulling and stretching the fabric of the prior surface_ to reflect where the true parameters likely live. More data means more pulling and stretching, and our original shape becomes mangled or insignificant compared to the newly formed shape. Less data, and our original shape is more present. Regardless, the resulting surface describes the _posterior distribution_.

![Prior probability recreated as the surface given p1~Exp\(3\), p2~Exp\(10\)](../../.gitbook/assets/image%20%2825%29.png)

![](../../.gitbook/assets/image%20%2818%29.png)

Notice that the posterior landscapes look different from one another, though the data observed is identical in both cases. The reason is as follows: the exponential-prior landscape puts very little _posterior_ weight on values in the upper right corner of the figure; this is because _the prior does not put much weight there_. On the other hand, the uniform-prior landscape is happy to put posterior weight in the upper-right corner, as the prior puts more weight there.

The black dot represents the true parameters. Even with 1 sample point, the mountains attempts to contain the true parameter. Of course, inference with a sample size of `1` is incredibly naive, and choosing such a small sample size was only illustrative.

## The MCMC landscape

Through this approach we may **find out the posterior mountains** \(and therefore the "best" parameters\). However, we cannot naively search over a _N-dimensional_ space, due to becomes a $$O(exp(N))$$ problem.  So, the idea behind MCMC is to **perform an intelligent and efficient search of the space**.

MCMC returns _samples_ from the posterior distribution, not the distribution itself. It performs a task similar to repeatedly asking "How likely is this point I found to be from the mountain I am searching for?", and completes its task by returning thousands of accepted points in hopes of reconstructing the original mountain.

### Algorithms to perform MCMC

There is a large family of algorithms that perform MCMC. However, they may be expressed as follows:

1. Start at current position
2. Propose moving to a new position $$\Rightarrow$$ Explore closer points
3. Based on the position's adherence to the data and prior distributions
   1. If accept: move to the new position. Return to Step 1
   2. If reject: don't move. Return to Step 1
4. After a large number of iterations, return all accepted positions.

This way we move in the general direction towards the regions where the posterior distributions exist, and collect samples sparingly on the journey. If the current position of the MCMC algorithm is in an area of extremely low probability, which is often the case when the algorithm begins, the algorithm will move in positions _that are likely not from the posterior_ but better than everything else nearby. Thus the first moves of the algorithm are not reflective of the posterior distribution.

  


