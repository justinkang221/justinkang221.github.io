---
title: "Efficiently Computing Sparse Fourier Transforms of q-ary Functions"
collection: publications
permalink: /publication/qFourier
excerpt: ''
date: 2023-01-15
venue:  'IEEE Int. Symp. Inf. Theory (ISIT)'
paperurl: 'https://ieeexplore.ieee.org/document/10206686'
citation: 'Kang, J., Erginbas*, Y. E., Agzazadeh, A., Ramchandran, K. (2023). &quot;Efficiently Computing Sparse Fourier Transforms of q-ary Functions&quot;.'
---

Abstract: Fourier transformations of pseudo-Boolean functions are popular tools for analyzing functions of
binary sequences. Real-world functions often have structures that manifest in a sparse Fourier transform,
and previous works have shown that under the assumption of sparsity the transform can be computed
efficiently. But what if we want to compute the Fourier transform of functions defined over a q-ary
alphabet? These types of functions arise naturally in many areas including biology. A typical workaround
is to encode the q-ary sequence in binary, however, this approach is computationally inefficient and
fundamentally incompatible with the existing sparse Fourier transform techniques. Herein, we develop
a sparse Fourier transform algorithm specifically for q-ary functions of length n sequences, dubbed
$q$-SFT, which provably computes an $S$-sparse transform with vanishing error as $q,n \rightarrow \infty$ in $O(Sn)$
function evaluations and $O(Sn^2 log q)$ computations, where $S = q$
$n\delta$ for some $\delta < 1$. Under certain
assumptions, we show that for fixed $q$, a robust version of $q$-SFT has a sample complexity of $O(Sn^2)$
and a computational complexity of $O(Sn^3)$ with the same asymptotic guarantees. We present numerical
simulations on synthetic and real-world RNA data, demonstrating the scalability of $q$-SFT to massively
high dimensional $q$-ary functions.


<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/_UgRE1iSrzY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
