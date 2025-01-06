---
title: Connection to Statistical Mechanics
layout: home
parent: Information and Entropy
nav_order: 2
---

## From Statistical Mechanics to Information Theory

Boltzmann introduced the idea of a [*statistical entropy*](https://en.wikipedia.org/wiki/Entropy), $$S$$ (which we will redefine as $$H$$ to match Shannon entropy while reserving $$S$$ for the Lagrangian action): 

$$H=k_B~\text{ln}~\Omega$$

where $$k_{B}$$ is known as the Boltzmann constant and $$\Omega$$ is the number of microstates that produces the same macroscopic properties (like energy, volume, pressure, temperature, ...). These microstates define a *statistical ensemble*. This formulation is only true under the assumption of *thermodynamic equilibrium* where the probability of each microstate is the same. Gibbs extended this definition to account for non-uniformly distributed ensembles as:

$$H = -k_B~\sum p_i~\text{ln}~p_i$$ 

which reduces to the Boltzmann formulation in thermodynamic equilibrium, e.g. $$p_i = 1 / \Omega$$.  Boltzmann/Gibbs entropy has units $$J\cdot K^{-1}$$ which then define the energy scale (in Joules) of the microstates at a given temperature (in Kelvin). 

Claude Shannon showed that [Information Entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)) *must* take the form 

$$H = - \sum p_i~\text{log}~p_i$$

in order to satisfy axioms requiring: continuity, additivity, and maximal entropy for uniform distribution. We can define $$\text{log}~p_i$$ as the *surprise* or *information content*. In computer science, $$\text{log}$$ is generally in base 2 so that the surprise is measured in *bits*. If $$\text{log}$$ is the natural logarithm then surprise is measured in *nats*. Entropy quantifies the expected/mean surprise. Shannon entropy plays an important role in communications as exemplified in Shannon's [*source coding theorem*](https://en.wikipedia.org/wiki/Shannon%27s_source_coding_theorem) which states that the minimum average number of bits per symbol to encode a source with entropy $$H$$ is at least $$H$$ bits. Shannon entropy represents the theoretical lower bound for lossless compression.  

As one might have already noticed, Gibbs entropy and Shannon entropy have the same form. According to Edwin Jaynes, the thermodynamic entropy is interpreted as being proportional to the amount of further Shannon information needed to define the detailed microscopic state of the system, that remains uncommunicated by a description solely in terms of the macroscopic variables of classical thermodynamics, with the constant of proportionality being just the Boltzmann constant[^1].

The above formulations of entropy by Boltzmann, Gibbs, and Shannon are only valid for classical systems. [*von Neumann entropy*](https://en.wikipedia.org/wiki/Von_Neumann_entropy) extends Gibbs entropy from classical statistical mechanics to quantum statistical mechanics. von Neumann entropy takes the form:

$$H = -\text{trace}(\rho~\text{ln}~\rho)$$ 

where $$\rho$$ is the density matrix which is needed to fully encode a mixed ensemble of quantum states. 

[^1]: [Jayne's Quote](https://en.wikipedia.org/wiki/Entropy_(information_theory)#:~:text=Relationship%20to%20thermodynamic%20entropy)

