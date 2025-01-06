---
title: Entropy and Surprise
layout: home
parent: Information and Entropy
nav_order: 1
---

## Information Entropy as a measure of average surprise

The probability of rolling a Heads in a fair coin is $$p=0.5$$. An observation of a single Heads is not *surprising*. How surprised would you be in an observation of 10 Heads from 10 rolls? It might be natural to feel 10 times as surprised. The concept of **surprisal** should be a function of probability with an additive nature. One function with this property is the negative logarithm. Let $$h_{i}$$ be the surprisal of outcome $$i$$:

$$h_{i}=-\text{log}p_{i}$$ 

where $$p_{i}$$ is the associated probability. The average, expected, surprisal is then

$$H = \mathbb{E}[h] = -\sum_{i}p_{i}h_{i} = -\sum_{i}p_{i}\text{log}p_{i}$$

which is defined as the ***entropy*** and is a property of a given probability distribution. If the dice were loaded on Heads then the average surprisal might not be as big. 

We can define the [*cross-entropy*](https://en.wikipedia.org/wiki/Cross-entropy):

$$H(p,q)=-\sum_{i}p_{i}\text{log}q_{i}$$

where $$q_i$$ and $$p_i$$ are the probabilities of outcome $$i$$ under distributions $$q$$ and $$p$$ where $$q$$ could be our belief in a fair dice and $$p$$ could represent the Heads-loaded dice. Cross-entropy allows us to quantify the expected surprise of a model $$q$$ used to approximate the true distribution $$p$$.

We can subtract the entropy of $$p$$ from the cross-entropy to arrive at the [*Kullback-Leibler divergence*](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence):

$$D_{KL} = H(p,q) - H(p) = -\sum_{i}p_{i}\text{log}q_{i} + \sum_{i}p_i\text{log}p_i = -\sum_{i}p_{i}\text{log}\frac{p_{i}}{q_{i}}$$

which measures the expected *additional* surprisal (over the base entropy from $$p$$). The KL divergence is a useful metric in constructing models, like neural networks, that minimize our surprise in how bad they are. It is always non-negative and equals zero if and only if $$p=q$$ everywhere and acts as a distance measure between two probability distributions. Note: the word "distance" is used loosely here since the KL divergence is not symmetric. 

Neural networks are *universal function approximators* which, when constructed to model probability distributions, can learn to model some target data distribution by minimizing the KL divergence. Note: the cross entropy is also used as there is only a difference of a constant, $$H(p)$$ which does not change the shape of the optimization landscape. KL-divergence is also used in [variational inference](https://en.wikipedia.org/wiki/Variational_Bayesian_methods).