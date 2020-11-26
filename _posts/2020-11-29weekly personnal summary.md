---
title: weekly personnal summary
tags: 周报
categories: 周报
---

## Documents

## Theories

- **Geometric-median**：针对向量，解一个凸优化问题，用一个估计所有向量
	- breakdown point = 0.5
	- Robutness of the Geometric Median (Lemma1 in [1])： 给出了geomedian 估计的值和真实值的差距
		- 定义**真实值**：定理中未定义，但可代表所有“干净样本”通过geomedian算出来的中值
		- 定义**估计值**：样本中含有恶意的vector，通过geomedian算出中值
		> - 在我们的算法中，先通过trim去除所有恶意样本，认为geomedian得到的都是“真实值”，这条robustness性质暂时无用？
- **Robustness property of our Alg.**
	- $hat{W}$ 和 $W_{trim}$的误差有直接的结论， see Theorem 3.1 in [2] and Theorem 1 in [1]
	>1. trim后再用geomedian没有必要？可以直接取平均(to reduce the variance in the estimation)。（这与之前的实验效果表现一致）
	>2. geomedian如果要用，不需要trim?
	> -  $W^* , \hat{W} $
- ==**Analysis of geometric median estimator of the population W^*** #9C27E2==
	- - [x] $\hat{W}$ 和 $W_{trim}$
		- robustness property 带有confidence，由 geometric median 带来的误差分析
	- - [ ] $W_{trim}$ 和 $W_{beforetrim}$
		- 差别在于排序
	- - [x] $W_{beforetrim}$和 $W^* $
		- $C=XX^T=\sum_{i\in[N]}X_iX_i^T=\sum_{i\in[N]}C_i$ -> $W^*$
			- 定义真实值 $W^* $ : centered data算出来的W
		- $C_1=\sum_{i\in[N]\B}X_iX_i^T=\sum_{i\in[N]\B}C_i$ -> $W_{beforetrim}$
		    - 定义 $W_{beforetrim}$： $W^* $中有些列有问题
		- $W^* $ 和 $W_{beforetrim}$的误差有直接的结论（DK theorem)
- **Convergence**: 
	- rate （<i class="fas fa-question"></i>需要分析吗


参考文献：
[1] Distributed Robust Learning
[2] Geometric median and robust estimation in banach spaces
## Experiments and results






## Reading
##### 1. A PROJECTION METHOD FOR LEAST SQUARES PROBLEMS WITH A QUADRATIC EQUALITY CONSTRAINT
- 解决LSQE问题，原问题：$min \|Ax-b\|_2~s.t.\|x\|_2=\alpha$
- ![enter description here](./images/1606114240410.png)
- projection method 

##### 2. A generalized power iteration method for solving quadratic problem on the Stiefel manifold
- 两个问题：
	- : $ max Tr(W^TAW)~s.t. W^TW=I $ $ \rightarrow $ GEP
	- Quadratic problem on the Stiefel manifold(QPSM)：$ min Tr(W^TAW-2W^TB)~s.t. W^TW=I $ 
- 两种算法：
	-  the power method （the dominant eigenvalue） 
	-  the orthogonal iteration method  (dominant eigenvalues)
- 两个应用：
	- Orthogonal least square regression
	- Unbalanced orthogonal procrustes problem

|  | PM|OI |
| :------:| :------: | :------: |
| QPSM | / | GPI (proposed) |
| GEP | PM | OI |

> <i class="fas fa-lightbulb"></i> 将GPI改为分布式 , $ M=UAV^T, W=UV^T $, 传vectors
> ||one-shot|multir-ound|
> |:---:| :------:| :------: |
> |in the central|average(W_i)| average($ W_i^t $)|
> |error analysis| | |

##### 3.Byzantine-Robust Distributed Learning: Towards Optimal Statistical Rates
- coordinate-wise 操作针对向量
	 > - 不同之处：文中的coordinate-wise median/mean 适合梯度，<i class="fas fa-question"></i>无法translated to eigenvector这边； geometric median适合向量（eigenvector）
- median-based GD
	- assumptions: bounded variance, skewness of gradient, smoothness of f and F
	- analysis: 
		- coordinate-wise median estimator of the population gradients
		- convergence of proposed algorithm


严格来说，我们一直做的都是类似于分布式机器学习的范围，主要考虑的是在基础机器学习算法（如PCA、CCA等）上设计分布式算法，其中在分布式PCA上已经有许多工作，而且基本上很多都是统计数学那边的人在做，我们也只是从那边拿一些结论过来加上自己的一点推导作为创新点。其中HF主要做的是kernel PCA的分布式算法，一方面因为在kernel方面有一些积累，另一方面从创新的角度比较容易。
和HF工作的不同之处在于，我一直想考虑一些应用场景类的东西，比如，通讯中断或者被攻击导致的传递信息的鲁棒性（进行中），带有隐私保护的信息传递，等。之前的第一篇关于DGEP的工作让我了解了这类文章的分析思路，以及学到了很多科研方法，在今后的工作中会思路更加清晰。