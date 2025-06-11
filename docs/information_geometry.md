---
title: Information Geometry
layout: home
nav_order: 3
---

A basic introduction to information geometry can be found in Reference [^1] with more detailed derivations and forms the basis of the following summary. This summary includes additional relevant insights.

# Differential Geometry (Riemannian)

Distances $$l$$ between coordinates $$x^i$$ and $$x^j$$ on a generic Riemannian **manifold** are defined by a **metric tensor**, $$g_{ij}$$, such that:

$$
dl^2 = g_{ij}dx^i dx^j
$$

which is Pythagoras' theorem in differential form derived from the observation that a curved manifold is locally flat. Let an infinitesimal displacement in this curved space from coordinate $$x^a \rightarrow \hat{x}^{\alpha}$$ be given by:

$$
d\hat{x}^{\alpha} = \frac{\partial\hat{x}^{\alpha}}{\partial x^a} dx^a = X^{\alpha}_{a} dx^a
$$

Then the infinitesimal volume element is given by:

$$
dV_n = g^{1/2}(x)d^n x
$$

where $$g = \text{det}(g_{ab}) = \vert \text{det}(X_a^{\alpha}) \vert^2$$ is the determinant of the Jacobian of the transformation squared. 

# Information Geometry

Let $$p_{\theta}(x)$$ be a probability distribution with parameters $$\theta = (\theta^1, ..., \theta^N)$$. The family of distributions $$\{p_{\theta}\}$$ forms a **statistical manifold** where each point, labeled with coordinates $$\theta$$, is a probability distribution. The distance between two nearby (on the statistical manifold) probability distributions is given by

$$
\Delta=\frac{p(x\mid\theta+d\theta)-p(x\mid\theta)}{p(x\mid\theta)}=\frac{\partial\log p(x\mid\theta)}{\partial\theta^a} d \theta^a
$$

Since we are talking about probability distributions one might think that the expectation value of $$\Delta$$, $$\left< \Delta \right>$$, could be used to distinguish local probability distributions but this quantity vanishes identically, $$\left< \Delta \right>=0$$. The variance, $$\left< \Delta^2 \right> - \left< \Delta \right>^2 = \left< \Delta^2 \right>$$, does not vanish:

$$
d \ell^2 = \left\langle\Delta^2\right\rangle = \int dx ~ p(x \mid \theta) \frac{\partial \log p(x \mid \theta)}{\partial \theta^a} \frac{\partial \log p(x \mid \theta)}{\partial \theta^b} d \theta^a d \theta^b := g_{ab}\theta^a d \theta^b
$$

Since the variance is strictly positive and only vanishes when $$d\theta$$ vanishes then the integral can be interpreted as a *metric tensor* and is known as the [Fisher information metric](https://en.wikipedia.org/wiki/Fisher_information_metric). Formally in words, the Fisher metric is the expected outer product of the gradient of the log-likelihood. The gradient of the log-likelihood is also known as the [**score**](https://en.wikipedia.org/wiki/Informant_(statistics)). This realization by [Rao](https://en.wikipedia.org/wiki/C._R._Rao) birthed the field of information geometry. Statistical manifolds have an inherent structure that inevitably leads to a **unique** notion of distance characterized by the information metric. 

A uniform probability distribution in curved space assigns equal probabilites to equal volumes
{: .note }

The distance between two nearby points on the statistical manifold is given by the Fisher metric and is approximately the KL divergence between the two distributions. See [variational inference](bayesian_inference/variational_inference.md) for more details.
{: .note }

# Inference

Inference provides a framework to find the optimal parameters, $$\theta_0$$, for a given model $$\mathcal{M}$$ describing some data $$x$$. The optimal parameters are found by minimizing a cost function, $$C(\theta)$$. 

In maximum likelihood estimation (MLE), the cost function is the (negative) log-likelihood, a scalar that quantifies the agreement between the model and the data. Every point on the statistical manifold, which represents the space of probability distributions, has an associated likelihood, giving rise to a likelihood surface. The point with the highest likelihood corresponds to the MLE solution.

The maximum likelihood solution is locally quadratic (gaussian) whose curvature is given by its **Hessian** which turns out to be equal to the negative Fisher metric (under some regularity conditions). See [this link for the derivation](https://math.stackexchange.com/questions/3585130/why-is-the-fisher-information-matrix-both-an-expected-outer-product-and-a-hessia)
{: .note }

In this context, the Fisher metric quantifies how much information the random variable $$x$$ (data) provides about the parameter vector $$\theta$$. At the MLE solution, the score (gradient of log-likelihood) fluctuates significantly around zero. A steeper likelihood surface corresponds to a greater variance in the score, which translates to a larger Fisher information metric. This indicates a well-constrained MLE solution, as the parameters are more precisely determined by the data as there is more *information*. See [Mutual Information Youtube Channel](https://www.youtube.com/watch?v=pneluWj-U-o) for graphical intuition on the Fisher information metric.

[^1]: [The Basics of Information Geometry](https://arxiv.org/pdf/1412.5633)
