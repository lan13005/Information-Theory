---
title: iftpwa - Default YAML
layout: home
parent: GlueX
nav_order: 2
---

# Correlated Field Model in NIFTy
Please read the following first, perhaps run the code yourself to see how the correlated field model works in NIFTy. This model forms the basis of the iftpwa package.
[Showcasingthe Correlated Field Model (NIFTy)](https://ift.pages.mpcdf.de/nifty/user/old_nifty_getting_started_4_CorrelatedFields.html)

The correlated field model is no longer a Gaussian process but it does make understanding and explaining the IFT approach easier
{: .note}

# Simplified Model

The following simplified model is used to depict how the configuration file key-value fields affect the physics model:

$$
\begin{align*}
& A_i = \kappa \cdot \rho_i \cdot C_i \cdot \left[ G(w_i, s_i, f_i, a_i) \times I(w_i) + a_i P_i(w_i, \vec{x}) \right] \\

& i = \textrm{wave index} \\ 
& \kappa = \textrm{kinematic factor} \\ 
& \rho_i = \textrm{phase space factor as a pkl file} \\
& C_i = \textrm{scale factor -> half-normal / laplace priors} \\
& G(s_i, f_i, a_i) = \textrm{Gaussian process with scale, flexibility, asperity} \\ 
& I = \textrm{indicator function to zero Gaussian process component} \\
& a = \textrm{prescale factor for Parametric component} \\
& P(\vec{x}) = \textrm{Parametric component with parameters } \vec{x} \\ 

\end{align*}
$$

# Default Configuration for GlueX PWA

Below is the default YAML configuration for GlueX analyses of $$\gamma p \rightarrow \eta\pi^0 p$$

{% capture config_content %}
{% include iftpwa_template.yaml %}
{% endcapture %}

```yaml
{{ config_content }}
```
