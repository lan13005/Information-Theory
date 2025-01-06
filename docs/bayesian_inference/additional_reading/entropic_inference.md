---
title: Entropic Inference
layout: home
grand_parent: Bayesian Inference
parent: Additional Reading
nav_order: 1
---

# Maximum Entropy methods

Ariel Caticha proposes the [Maximum Entropy method](https://arxiv.org/pdf/2107.04529) which unifies entropic and Bayesian methods into the same inference framework. 

Summary as follows:

What is information? A pragmatic answer according to Caticha is "Information is that which induces a change from one state of rational belief to another." In the context of Bayesian inference, the posterior is the result of an update to the prior by the information contained in the data. 

A *rational belief system* can be constructed based on three key design principles: universality, the Principle of Minimal Updating (PMU), and independence. 
- *Universality* ensures that the method applies to any problem with arbitrary priors and constraints.
- *PMU* dictates that belief updates should minimally deviate from prior information unless explicitly contradicted by new information, thereby acting like an *inertia*. 
- *Independence* enforces the idea that systems assumed to be independent remain so unless new evidence explicitly introduces correlations. 

This rational belief system should have a ranking scheme from which the optimal posterior is the one that is maximally "preferred". The Maximum Entropy method singles out the *KL divergence*, or relative entropy functional, between the posterior and prior probability distributions as the ranking metric. Other known forms of entropy do not satisfy all three design principles. 

A significant outcome of the ME framework is that *Bayes' rule naturally emerges as a special case*. However, the ME method extends beyond Bayes' rule to situations where standard Bayesian techniques falter, such as cases of uncertain data or even unknown likelihoods. Additionally, the ME method provides a prescription to obtain a modified posterior that considers all posterior distributions weighted by the exponential of their entropy. This modification reduces to the standard ME approach if the maximum entropies of the posteriors are sharply peaking.