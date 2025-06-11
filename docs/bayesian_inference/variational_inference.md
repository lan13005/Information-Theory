---
title: Variational Inference
layout: home
parent: Bayesian Inference
nav_order: 1
---

# Marginal Likelihood and Variational Inference

The marginal likelihood represents the total probability of observing the data $$x$$ under a model $$\mathcal{M}$$, averaging over all latent variables and parameters. It tells us how well the **entire model class** explains the data, balances **data fit** (likelihood) with **model complexity** (prior volume), and serves as an objective for **model comparison** and **model selection**.

In Bayesian models with latent variables $$z$$, the marginal likelihood (also known as the evidence) of observed data $$x$$ is:

$$
\log p(x) = \log \int p(x, z) \, dz
$$

In variational inference, we introduce a tractable variational distribution $$q(z)$$ to approximate the intractable posterior $$p(z \mid x)$$.

### Importance Sampling View

We begin with the following identity:

$$
p(x) = \int p(x, z) \, dz = \int q(z) \frac{p(x, z)}{q(z)} \, dz = \mathbb{E}_{q(z)}\left[ \frac{p(x, z)}{q(z)} \right]
$$

where $$\frac{p(x, z)}{q(z)}$$ are the **importance weights**.

Applying **Jensen's inequality** to this expression yields:

$$
\log \mathbb{E}_{q(z)}\left[ \frac{p(x, z)}{q(z)} \right] \geq \mathbb{E}_{q(z)}\left[ \log \frac{p(x, z)}{q(z)} \right]
$$

The right-hand side defines the **Evidence Lower Bound (ELBO)**. This lower bound has desirable properties that make it suitable as an optimization objective:

- **Numerically stable**: The logarithm is applied before averaging, reducing sensitivity to outliers in importance weights.
- **Differentiable**: The expectation of a log allows for backpropagation through **reparameterized samples**.
- **Log of average** (outside) is difficult to differentiate and has higher variance in Monte Carlo estimation.

We can recover an exact expression for the marginal likelihood by adding the **Kullback–Leibler (KL) divergence** term to the ELBO. This gives the **ELBO decomposition**:

$$
\log p(x) = \underbrace{\mathbb{E}_{q(z)}\left[\log \frac{p(x, z)}{q(z)}\right]}_{\text{ELBO}} + \underbrace{\mathrm{KL}(q(z) \| p(z \mid x))}_{\geq 0}
$$

For more information on KL divergence, see the [introduction to surprisal](../information_and_entropy/surprisal.html). The marginal likelihood is equal to the ELBO if and only if the variational distribution $$q(z)$$ exactly matches the true posterior $$p(z \mid x)$$.

## KL Divergence and the Fisher Metric

If you have read [information geometry](../information_geometry.html) it is interesting to make a connection between the KL divergence and the **Fisher information metric**. In the limit where two distributions differ by an infinitesimal change in parameters, the KL divergence between them approximates the squared geodesic distance under the Fisher information metric.

Consider the KL divergence between $$p(x\mid\theta)$$ and a nearby distribution $$p(x\mid\theta + d\theta)$$:

$$
D_{\mathrm{KL}}(p(x\mid\theta) \| p(x\mid\theta + d\theta)) = \int dx ~ p(x\mid\theta) \log \frac{p(x\mid\theta)}{p(x\mid\theta + d\theta)}
$$

Expanding the logarithm to second order:

$$
\log p(x\mid\theta + d\theta) = \log p(x\mid\theta) + d\theta^a \partial_a \log p(x\mid\theta) + \frac{1}{2} d\theta^a d\theta^b \partial_a \partial_b \log p(x\mid\theta) + \dots
$$

where $$\partial_a \equiv \frac{\partial}{\partial \theta^a}$$. Note: $$\log p(x\mid\theta)$$ cancels with the same term in $$D_{\mathrm{KL}}$$ and the expectation value of the first order expansion term vanishes identically as before. The KL divergence is then:

$$
\begin{align*}
D_{\mathrm{KL}}(p(x\mid\theta) \| p(x\mid\theta + d\theta)) 
&= \frac{1}{2} d\theta^a d\theta^b \int dx ~ p(x\mid\theta) \, \partial_a \log p(x\mid\theta) \, \partial_b \log p(x\mid\theta) \\
&\quad + \dots \\
&= \frac{1}{2} g_{ab} d\theta^a d\theta^b + O(\|d\theta\|^2)
\end{align*}
$$

and is equal to one-half the squared distance on the statistical manifold.