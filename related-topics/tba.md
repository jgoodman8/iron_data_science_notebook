# Combinatorics

{% hint style="info" %}
_Sources:_

* \_\_[_Combinatorics \(Mathigon\)_](https://mathigon.org/world/Combinatorics)\_\_
* \_\_[_Combinations and Permutation \(Math is Fun\)_](https://www.mathsisfun.com/combinatorics/combinations-permutations.html)\_\_
* \_\_[_Math Stack Exchange Question_](https://math.stackexchange.com/questions/208377/combination-with-repetitions)\_\_
{% endhint %}

## All about order and repetition

{% hint style="success" %}
**Combination** $$\Rightarrow$$when the order does not matter

**Permutation** $$\Rightarrow$$ when the order does matter
{% endhint %}

## Permutations

### With repetition

If we wish to know the **number of combinations of a PIN number**, we have 10 chances per digit \(due to numbers from 0 to 9\).



So, we got $$10 \cdot 10 \cdot 10 \cdot 10$$ possibilities \($$n \cdot n \cdot n \cdot n$$\). Thus, generalizing we get the formula:

$$
N^R   \\ R\text{ items selected out of } N
$$

### With no repetition

If what to know all the **order of** _**N**_ **pool balls be in,** for each ball taken we have $$ N_{i+1} = N_i - 1 $$ possibilities.

![](../.gitbook/assets/image%20%2814%29.png)

Generalizing, we get:

$$
\frac{N!}{(N-R)!} \\ R \text{ items selected out of } N \text{ with no repetition}
$$

In the particular case, that _**R**_ **is equal to** _**N**_, we get up to _**N!**_ possibilities.

## Combinations

### With no repetition

Here, we can discover the number of possible results in lotteries. We take _**R from**_ ****_**N**_ **unique items.** However, we **don't mind the order** of the taken items.

![](../.gitbook/assets/image%20%2874%29.png)

We have to divide the possible $$N!$$ __elements by the $$(N-R)!$$ possible repetitions and the $$R!$$ possible combination of the taken items. This is expressed as:

$$
C(n, r) = nCr = \binom{N}{R} = \frac{N!}{R!(N-R)!}
$$

### With repetition

This problem comes by many names - stars and stripes, balls and urns - it's basically a question of how to distribute $$N$$ objects \(call them "balls"\) into $$R$$ categories \(call them "urns"\). We can think of it as follows.

Take $$N$$ balls and $$R-1$$ dividers. If a ball falls between two dividers, it goes into the corresponding urn. If there's nothing between two dividers, then there's nothing in the corresponding urn. Let's look at this with a concrete example.

I want to distribute 5 balls into 3 urns. As before, take 5 balls and 2 dividers. Visually:

> \|ooo\|oo

In this order, we'd have nothing in the first urn, three in the second urn and two balls in the third urn. The question then is how many ways can we arrange these 5 balls and two dividers?

$$
\binom{R+N-1}{R}  = \binom{R+N-1}{N-1} = \frac{(R+N-1)!}{R! (N-1)!}
$$

