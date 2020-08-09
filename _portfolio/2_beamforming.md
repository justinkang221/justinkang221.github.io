---
title: "Off-Grid Compressed Sensing for mmWave Channel Estimation"
excerpt: "Sparse signal processing, but without quantization noise! <br/><img src='/images/blkdiagram.png'>"
collection: portfolio
---

We consider the problem of channel estimation in millimeter wave massive multiple-input multiple-output systems with a hybrid architecture. The existing strategies for channel estimation hinge on the use of a grid of finite resolution from which the angles of departure are taken. Unlike those strategies, we investigate a grid-less channel estimation approach does not assume that the angles come from a finite resolution grid, but rather are continuous variables. This underlying optimization problem can be reformulated as an exact semi-definite program for which efficient solvers are readily available. Numerical comparisons suggest that the performance of the off-grid scheme is better than that of the grid-base counterparts when the number of grid points is of the same order as the number of antennas. In this regime grid-based solutions suffer from the error floor associated with restricting the angle of departure to a discrete grid of finite resolution, while the off-grid scheme does not. In addition, computational complexity analysis reveal that these performance gains are realized only at the cost of a modest increase in complexity relative to the most widely-known grid-based algorithms.

<a href="https://justinkang221.github.io/files/ECE1505_Project.pdf">Paper
here</a>
