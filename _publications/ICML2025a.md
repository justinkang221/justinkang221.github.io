---
title: "SPEX: Scaling Feature Interaction Explanations for LLMs"
collection: publications
permalink: /publications/spex-scaling-feature-interactions
excerpt: ''
date: 2025-02-10
venue: Preprint
paperurl: 'https://arxiv.org/abs/2502.13870'
citation: 'Kang, J.S., <a href="https://aagarwal1996.github.io/">Agarwal, A.,</a>  <a href="https://erginbas.github.io/">Erginbas, Y.E.</a>, <a href="https://landonbutler.github.io/">Butler, L.</a>, <a href="https://web.ece.ucsb.edu/~ramtin/">Pedarsani, R.</a>, <a href="https://people.eecs.berkeley.edu/~kannanr/">Ramchandran, K.</a> &quot; SPEX: Scaling Feature Interaction Explanations for LLMs'
---

<img src="/images/interaction_diagram.png">


<a href='https://justinkang221.github.io/files/SPEX_Poster.pdf'>Poster</a>

Abstract: Large language models (LLMs) have revolutionized machine learning due to their ability to capture complex interactions between input features. Popular post-hoc explanation methods like SHAP provide marginal feature attributions, while their extensions to interaction importances only scale to small input lengths (≈20). We propose Spectral Explainer (SPEX), a model-agnostic interaction attribution algorithm that efficiently scales to large input lengths (≈1000). SPEX exploits underlying natural sparsity among interactions -- common in real-world data -- and applies a sparse Fourier transform using a channel decoding algorithm to efficiently identify important interactions. We perform experiments across three difficult long-context datasets that require LLMs to utilize interactions between inputs to complete the task. For large inputs, SPEX outperforms marginal attribution methods by up to 20% in terms of faithfully reconstructing LLM outputs. Further, SPEX successfully identifies key features and interactions that strongly influence model output. For one of our datasets, HotpotQA, SPEX provides interactions that align with human annotations. Finally, we use our model-agnostic approach to generate explanations to demonstrate abstract reasoning in closed-source LLMs (GPT-4o mini) and compositional reasoning in vision-language models.  
