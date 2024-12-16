---
title: Heisenberg to Entropic Uncertainty
layout: home
parent: Additional Reading
nav_order: 3
---

# Entropic Uncertainty

Interestingly information theory can be used to derive a more rigorous limit than the **Heisenberg Uncertainty Principle** which is a statement about how precisely we can measure conjugate variables like position and momentum of a particle. Position and momentum are Fourier transform pairs (not all conjugate variables are!). Then the continuous form of Entropy, the *differential entropy*, takes the form:

$$H(p(x)) = \int p(x) \text{log} p(x)dx \quad \text{and} \quad H(p(p)) = \int p(p) \text{log} p(p)dp$$

where $$H(p(p))$$ is the Fourier transformed pair. $$p(p)$$ is the momentum probability distribution. The [Entropic Uncertainty](https://en.wikipedia.org/wiki/Entropic_uncertainty) is given by

$$H(p(x)) + H(p(p)) \geq 1 + \text{log}(2\pi\hbar)$$

where $$\hbar$$ is the reduced Planck constant. Heisenberg uncertainty principle uses the Gaussian approximated standard deviation whereas the Entropic uncertainty considers the entire probability distribution and is therefore a more accurate statement.
