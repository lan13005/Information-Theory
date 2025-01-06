---
title: Information Field Theory
layout: home
parent: Bayesian Inference
nav_order: 1
---

# Information Field Theory and Bayesian Analysis

## Bayesian Analysis

Bayesian analysis provides a rigorous statistical framework for inferring the properties of a system by updating our prior knowledge with observational data. At its core lies Bayes theorem, which relates the posterior probability $$P(s\vert d)$$ of a signal $$s$$ given data $$d$$, to the likelihood $$P(d\vert s)$$ and prior $$P(s)$$ as:

$$ P(s\vert d) = \frac{P(d\vert s) P(s)}{P(d)}$$

Bayesian inference on spatially distributed fields can be recast in the language of information theory allowing one to leverage existing tools and concepts from quantum field theory and statistical mechanics. This reformulation is known as [Information Field Theory (IFT)](https://en.wikipedia.org/wiki/Information_field_theory). 

## Quantum and Statistical Field Theories and the Partition Function

Special relativity describes the connection between space and time for inertial observers and forms a cornerstone of modern physics, including quantum field theory. Physical theories can be expressed in terms of forces but are often derived from scalar quantities such as the [Lagrangian](https://en.wikipedia.org/wiki/Lagrangian_mechanics#:~:text=Lagrangian%20mechanics%20describes%20a%20mechanical,energy%20of%20the%20system%2C%20respectively.) and [Hamiltonian](https://en.wikipedia.org/wiki/Hamiltonian_mechanics). 

It turns out that the Lagrangian is a more suitable quantity than the Hamiltonian in modern physics due to the nature of special relativity. The Hamiltonian determines time evolution but time is reference frame dependent. On the other hand, the Lagrangian is a Lorentz scalar. Therefore, relativistic quantum field theories tend to use the Lagrangian formalism. 

Suppose a *classical* particle is initially at coordinates $$x_i$$ and ends at $$x_f$$. The **principle of stationary action** states that the path the particle takes is the one that has a stationary action (defined later). The *quantum* analogue to the principle of stationary action is the [**path integral formalism**](https://en.wikipedia.org/wiki/Action_principles#:~:text=%5D%3A%E2%80%8A138-,Feynman%27s%20action%20principle,-%5Bedit%5D) where a particle takes all possible paths between the two coordinates weighted by the probability amplitude. Other paths will have phases that changes rapidly and therefore do not have a large amplitude (or contribution).

The *classical action*, $$S$$, is defined using the Lagrangian as:

$$
S = \int \mathcal{D}x \mathcal{L}
$$

where $$\int \mathcal{D}x$$ is a path integral over field coordinates (i.e. spacetime) and $$\mathcal{L}$$ is the Lagrangian. Assuming natural units where $$\hbar=1$$, the path integral takes the form:

$$
\psi(x) = \frac{1}{\mathcal{Z}}\int \mathcal{D}x e^{iS}\psi_0(x)
$$

where $$\mathcal{Z}$$ is known as the **partition function** (which was first used to describe statistical mechanics). Knowing the partition function (in both quantum field theory and statistical mechanics) completely specifies the system allowing all relevant quantities to be derived from it. The partition function is defined as:

$$
\mathcal{Z} = \int \mathcal{D}x e^{iS}
$$

A parallel can be drawn to [statistical field theory](https://en.wikipedia.org/wiki/Statistical_field_theory) by [Wick rotating](https://en.wikipedia.org/wiki/Wick_rotation) to imaginary time thereby reformulating $$\mathcal{Z}$$ from [Minkowski Space](https://en.wikipedia.org/wiki/Minkowski_space) to Euclidean space. This allows many results from statistical field theory and quantum field theory to be shared.

The *statistical field theory partition function* can be slightly reformulated to be a *generating functional* by introducing a source term, $$J(x)$$:

$$
\mathcal{Z} = \int \mathcal{D}x e^{-[S+\int dxJ(x)\phi(x)]}
$$

from which arbitrary $$n$$-point [correlation functions](https://en.wikipedia.org/wiki/Correlation_function#) can be derived (generated) from by taking $$n$$ functional derivatives of $$J(x)$$ evaluated at $$J=0$$, see [Ref.](https://en.wikipedia.org/wiki/Partition_function_(quantum_field_theory)#:~:text=%5Bedit%5D-,Scalar%20theories,-%5Bedit%5D) for derivation. For $$\mathcal{Z}$$ to converge  $$e^{-S}$$ must converge. This requires that $$S$$ and therefore $$\mathcal{L}$$ to be bounded from below. The *statistical mechanics partition function*, in the *canonical ensemble*, takes the form:

$$
\mathcal{Z} = \int e^{-\beta \mathcal{H}}
$$

where $$\mathcal{H}$$ is the Hamiltonian, describing the total energy of the system. The similarity in form of the statistical mechanics partition function and the statistical field theory partition function and the fact that Euclidean $$\mathcal{L}$$ is bounded from below allows $$\mathcal{L}$$ to be interpreted as an energy density and $$S$$ as an energy. 

Another useful generating functional is the logarithm of the partition function: $$W[J] = -i\text{ln}Z[J]$$ which takes a similar form as the [Helmholtz Free Energy](https://en.wikipedia.org/wiki/Helmholtz_free_energy#:~:text=Microscopic%20definition%20of). A [Legendre Transformation](https://en.wikipedia.org/wiki/Legendre_transformation) can be performed on $$W[J]$$ to create a functional that depends on the mean field $$\phi(x)$$ and is known as the [*quantum effective action*](https://en.wikipedia.org/wiki/Effective_action):

$$
\Gamma[\phi] = W[J] - \int dx J(x) \phi(x)
$$

Legendre transformation of the statistical mechanics Helmholtz free energy can be used to derive the [Gibbs Free Energy](https://en.wikipedia.org/wiki/Gibbs_free_energy). 

Following this parallel, the QFT effective action can be seen as a Gibbs free energy which is a Legendre transformation of the Helmholtz free energy. The effective action is the quantum analogue of the classical action and includes the necessary quantum corrections such that applying the principle of stationary action on quantum fields produces the correct equations of motion.
{: .note }

## Information Field Theory 

In IFT, the posterior probability $$P(s\vert d)$$ is expressed in the familiar form of statistical mechanics as:

$$
P(s\vert d) = \frac{e^{-H[s]}}{Z}
$$

where $$H[s]$$ and $$Z$$ is known as the *information Hamiltonian* and the partition function respectively. These are defined as:

$$
H[s] = -\log P(d\vert s) - \log P(s) \quad \text{and} \quad
Z = \int \mathcal{D}s \, e^{-H[s]}
$$

where $$\int \mathcal{D}s$$ defines a path integral. It is convenient to redefine $$Z$$ as we have done above:

$$
Z[J] = \int \mathcal{D}s\exp^{-\mathcal{H}[s]+J^{\dagger}s}
$$

where the old partition function can be recovered by setting $$J=0$$. Doing so allows one to calculate any moment (see [moment generating function](https://en.wikipedia.org/wiki/Moment-generating_function)) of the signal field by evaluating derivatives of the new partition function at $$J=0$$:

$$
\left< s(x_1) \cdot \cdot \cdot s(x_n) \right> = \frac{1}{\mathcal{Z}}\frac{\delta^nZ[J]}{\delta J(x_1) \cdot \cdot \cdot  \delta J(x_n)} \Big\vert _{J=0}
$$

Here, the second-order moment corresponds to a correlation between two points and is known as a two-point [correlation function](https://en.wikipedia.org/wiki/Correlation_function#). For a field with zero mean, the two-point correlation function is equal to the covariance. 

Fields can have infinite number of degrees of freedom but physical ones are generally smooth and continuous (as large differences in nearby field points can be energetically unfavorable, i.e. electic fields, and are often rapidly erased through difussive processes, i.e. temperature). Therefore, a finite dimensional set of measurement data must be coupled with properly constraining prior knowledge/specification (for example in the form of field correlations). 

These fields can be consistently discretized (or pixelated) to describe the typical data measurement process by integrating the continuous field in every discretized subdomain. In this context, consistency means that the discretization scheme preserves the continuum limit. 

A free IFT can be constructed for a data field $$d$$ generated by a linear response $$R$$ to a Gaussian signal $$s$$ with two-point correlation function $$S$$ with an additional zero-mean Gaussian noise field $$n$$ with covariance $$N$$ as

$$d = Rs + n$$ 

The Gaussian fields are [Gaussian Processes](https://en.wikipedia.org/wiki/Gaussian_process). The information Hamiltonian for this processes is denoted $$\mathcal{H}_{free}$$. The posterior mean of this free IFT is given by 

$$m=Dj$$ 

where $$D=(S^{-1} + R^{\dagger}N^{-1}R^{-1})$$ and $$j=R^{\dagger}N^{-1}d$$ see [Ref.](https://en.wikipedia.org/wiki/Information_field_theory#:~:text=a%20free%20IFT.-,Free%20theory,-%5Bedit%5D) for the derivation. $$m$$ is known as the [generalized Wiener filter](https://en.wikipedia.org/wiki/Generalized_Wiener_filter) solution. In the IFT context, $$j$$ is known as an *information source* and $$D$$ is the *information propagator*. By Taylor expanding the information Hamiltonian, a process with a non-linear $$R$$ or non-Gaussian $$s$$ or $$n$$ can be described by a Hamiltonian that includes and interaction term:

$$\mathcal{H}(d, s) = \mathcal{H}_{\text{free}}(d, s) + \mathcal{H}_{\text{int}}(d, s)$$

where $$\mathcal{H}_{\text{free}}(d, s)$$ contains the Gaussian posterior derived above and $$\mathcal{H}_{\text{int}}(d, s)$$ contains non-Gaussian corrections. If the non-Gaussian corrections are small then $$\mathcal{H}(d, s)$$ can be studied perturbatively, for example using Feynman diagrams. 

The Wiener filter solution requires the knowledge of the two-point correlation function of the signal. If this quantity is not known a prior then it must be inferred from data along with the field itself. By the [Wiener–Khinchin theorem](https://en.wikipedia.org/wiki/Wiener%E2%80%93Khinchin_theorem), if the random field is stationary (invariant under translations) then it is sufficient to only infer the power spectrum. That is, the two-point correlation function and the power spectrum are Fourier transform pairs.

In statistical mechanics the [Helmholtz Free Energy](https://en.wikipedia.org/wiki/Helmholtz_free_energy#:~:text=Microscopic%20definition%20of), $$F$$, is the log of the partition function

$$
F = -kT\log Z = U - TS
$$

which is then related to [cumulants](https://en.wikipedia.org/wiki/Cumulant) which are the log of the moment generating functions. $$U, T, S$$ are the internal energy, temperature, and entropy of the system. 

The thermodynamic [Gibbs Free Energy](https://en.wikipedia.org/wiki/Gibbs_free_energy) is given by $$U-TS+PV$$.  The $$PV$$ term describes work done at constant pressure and does not have a meaningful interpretation in IFT. As we have previously Noted above, the Gibbs free energy shares a similar form to the QFT effective action. It turns out that minimizing the Gibbs Free Energy is the same as minimizing the [Kullback-Leibler divergence](entropy), KL divergence, between the approximate and exact posterior, see [Ref.](https://en.wikipedia.org/wiki/Information_field_theory#:~:text=Early%20Universe.-,Effective%20action,-%5Bedit%5D) for derivation. The effective action analogue in IFT is equivalent to variational Bayes approaches that use the KL divergence.

## References
[Wikipedia: Information Field Theory](https://en.wikipedia.org/wiki/Information_field_theory)
[Information theory for fields](https://arxiv.org/abs/1804.03350)