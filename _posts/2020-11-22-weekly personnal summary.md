---
title: 2020-11-17-weekly personnal summary
tags: 周报
---
## Documents
- - [ ] proposal of experiments of Byzantine PCA
- - [ ] unbalanced Procrustes
- - [x] introduction of DGEP
	- 增加了Lagrangian，同时改变公式顺序，使推导更完整
	-  related work 上下文的逻辑性整理
## Experiments
#### SGCCA
- - [x] EB-zero
- - [x] EB-eigen
#### Byzantine PCA
- - [ ] DPCA-multiround
- - [ ] Byzantine PCA-multiround
## Results






## Reading
#### Distributed Robust Learning


#### Successive projection method for solving the unbalanced Procrustes problem
- unbalanced Proctustes problems
	- nonconvex problem on Stiefel manifold
	- **unbalanced**： min || A- BQ||_F , A,B不同维 ，相比于balanced的形式没有闭式解 
- algorithms
	- Expansion-Balance (EB)
	- Successive Projection (SP)  (proposed)
	- Left side relaxation algorithm (LSR)