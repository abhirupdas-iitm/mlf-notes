## Lecture 1
### Principal Component Analysis Part 1

### Motivation and Overview

Principal Component Analysis is a dimensionality reduction technique used for feature selection.
Given high dimensional data, the goal is to project the data onto a lower dimensional subspace such that:
1. Reconstruction error is minimized.
2. Variance of projected data is maximized.
In this lecture, we adopt the first viewpoint.

---
### Problem Formulation

#### Dataset
Let the dataset be
$$
D = \{ x_1, x_2, \dots, x_n \}, \quad x_i \in \mathbb{R}^d
$$
#### Goal
Project the dataset onto an $m$-dimensional subspace, where $m < d$ is fixed in advance.

---
### Step 1: Fix an $m$-Dimensional Subspace

Let
$$
B = \{ u_1, \dots, u_m \}
$$
be an orthonormal basis for an $m$-dimensional subspace of $\mathbb{R}^d$.
Extend $B$ to a full orthonormal basis
$$
B' = \{ u_1, \dots, u_m, u_{m+1}, \dots, u_d \}
$$
for $\mathbb{R}^d$.

---
### Representation of Data Points

Since $B'$ is an orthonormal basis, any $x \in \mathbb{R}^d$ can be written as
$$
x = \sum_{j=1}^{d} (x^T u_j) u_j
$$
In particular,
$$
x_i = \sum_{j=1}^{d} (x_i^T u_j) u_j
$$
---
### Projection onto the $m$-Dimensional Subspace

Approximate $x_i$ by $\tilde{x}_i$:
$$
\tilde{x}_i = \sum_{j=1}^{m} z_{ij} u_j + \sum_{j=m+1}^{d} \beta_j u_j
$$
where $z_{ij}$ and $\beta_j$ are coefficients to be determined.

---
#### Reconstruction Error

Define the reconstruction error:
$$
J = \frac{1}{n} \sum_{i=1}^{n} \| x_i - \tilde{x}_i \|^2
$$
Substituting expansions,
$$
x_i - \tilde{x}_i
=
\sum_{j=1}^{m} (x_i^T u_j - z_{ij}) u_j
+
\sum_{j=m+1}^{d} (x_i^T u_j - \beta_j) u_j
$$
Since $\{ u_j \}$ is orthonormal,
$$
\left\|
\sum c_j u_j
\right\|^2
=
\sum c_j^2
$$
Thus,
$$
J
=
\frac{1}{n}
\sum_{i=1}^{n}
\left[
\sum_{j=1}^{m} (x_i^T u_j - z_{ij})^2
+
\sum_{j=m+1}^{d} (x_i^T u_j - \beta_j)^2
\right]
$$
---
### Minimizing with Respect to $z_{ij}$
Compute
$$
\frac{\partial J}{\partial z_{ij}} = 2 (x_i^T u_j - z_{ij}) = 0
$$
Hence,
$$
z_{ij} = x_i^T u_j
$$
---
### Minimizing with Respect to $\beta_j$

Compute
$$
\frac{\partial J}{\partial \beta_j}
=
\frac{2}{n}
\sum_{i=1}^{n}
(x_i^T u_j - \beta_j)
=
0
$$
Thus,
$$
\beta_j
=
\frac{1}{n}
\sum_{i=1}^{n}
x_i^T u_j
$$
Define the sample mean:
$$
\bar{x}
=
\frac{1}{n}
\sum_{i=1}^{n}
x_i
$$
Then,
$$
\beta_j = \bar{x}^T u_j
$$
---
### Optimal Projection

With optimal coefficients,
$$
\tilde{x}_i
=
\sum_{j=1}^{m}
(x_i^T u_j) u_j
+
\sum_{j=m+1}^{d}
(\bar{x}^T u_j) u_j
$$
If data is centered,
$$
\bar{x} = 0
$$
and the second term vanishes:
$$
\tilde{x}_i
=
\sum_{j=1}^{m}
(x_i^T u_j) u_j
$$
---
### Expression for Reconstruction Error

Compute
$$
x_i - \tilde{x}_i
=
\sum_{j=m+1}^{d}
(x_i^T u_j - \bar{x}^T u_j) u_j
$$
Thus,
$$
\| x_i - \tilde{x}_i \|^2
=
\sum_{j=m+1}^{d}
((x_i - \bar{x})^T u_j)^2
$$
Hence optimal error:
$$
J^*
=
\frac{1}{n}
\sum_{i=1}^{n}
\sum_{j=m+1}^{d}
((x_i - \bar{x})^T u_j)^2
$$
Interchanging summations,
$$
J^*
=
\frac{1}{n}
\sum_{j=m+1}^{d}
\sum_{i=1}^{n}
((x_i - \bar{x})^T u_j)^2
$$
Write as quadratic form:
$$
((x_i - \bar{x})^T u_j)^2
=
u_j^T (x_i - \bar{x})(x_i - \bar{x})^T u_j
$$
Define covariance matrix:
$$
C
=
\frac{1}{n}
\sum_{i=1}^{n}
(x_i - \bar{x})(x_i - \bar{x})^T
$$
Then,
$$
J^*
=
\sum_{j=m+1}^{d}
u_j^T C u_j
$$
---
### Key Result

For a fixed $m$-dimensional subspace with orthonormal basis $\{ u_1, \dots, u_m \}$,
the reconstruction error is
$$
J^*
=
\sum_{j=m+1}^{d}
u_j^T C u_j
$$
where
$$
C
=
\frac{1}{n}
\sum_{i=1}^{n}
(x_i - \bar{x})(x_i - \bar{x})^T
$$
This reduces PCA to choosing the basis vectors $\{ u_j \}$ so as to minimize
$$
\sum_{j=m+1}^{d}
u_j^T C u_j
$$
which leads to the eigenvalue formulation of PCA.

---
`***********************************************************************************`

---
## Lecture 2 
### Principal Component Analysis Efficient Implementation

### High Dimensional Setting
Given dataset
$$
\{ x_1, x_2, \dots, x_n \}, \quad x_i \in \mathbb{R}^d
$$
Assume
$$
d \gg n
$$
Standard PCA requires eigen-decomposition of covariance matrix
$$
C = \frac{1}{n} \sum_{i=1}^{n} (x_i - \bar{x})(x_i - \bar{x})^T
$$
where
$$
\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_i
$$
Here,
$$
C \in \mathbb{R}^{d \times d}
$$
Computing eigenvalues of a $d \times d$ matrix is computationally expensive when $d$ is large.

---
### Rank Observation
Each matrix
$$
(x_i - \bar{x})(x_i - \bar{x})^T
$$
is rank one.
Thus,
$$
\operatorname{rank}(C) \le n
$$
Therefore,
$$
d - n
$$
eigenvalues of $C$ are zero.
It is unnecessary to compute all $d$ eigenvectors.

---
### Matrix Reformulation

Define matrix
$$
A =
\begin{bmatrix}
(x_1 - \bar{x})^T \\
(x_2 - \bar{x})^T \\
\vdots \\
(x_n - \bar{x})^T
\end{bmatrix}
$$
Then,
$$
C = \frac{1}{n} A^T A
$$
where
$$
A \in \mathbb{R}^{n \times d}
$$
---
### Key Observation

Instead of computing eigenvectors of
$$
\frac{1}{n} A^T A
$$
which is $d \times d$, compute eigenvectors of
$$
\frac{1}{n} A A^T
$$
which is $n \times n$.

---
### Eigenvalue Correspondence

Let
$$
C u_i = \lambda_i u_i
$$
where
$$
C = \frac{1}{n} A^T A
$$
Then,
$$
\frac{1}{n} A^T A u_i = \lambda_i u_i
$$
Multiply both sides by $A$:
$$
\frac{1}{n} A A^T (A u_i) = \lambda_i (A u_i)
$$
Thus,
$$
\lambda_i
$$
is an eigenvalue of
$$
\frac{1}{n} A A^T
$$
---
### Reverse Direction

Let
$$
\frac{1}{n} A A^T v_i = \lambda_i v_i
$$
Multiply by $A^T$:
$$
\frac{1}{n} A^T A (A^T v_i) = \lambda_i (A^T v_i)
$$
Thus,
$$
A^T v_i
$$
is an eigenvector of
$$
C = \frac{1}{n} A^T A
$$
with eigenvalue $\lambda_i$.

---
### Efficient PCA Algorithm

When $d \gg n$:
1. Form matrix
$$
A \in \mathbb{R}^{n \times d}
$$
2. Compute eigenvalues and eigenvectors of
$$
\frac{1}{n} A A^T \in \mathbb{R}^{n \times n}
$$
3. Recover eigenvectors of covariance matrix using
$$
u_i = A^T v_i
$$
4. Normalize $u_i$

---
### Connection to SVD

Since
$$
A = U \Sigma V^T
$$
then
$$
A^T A = V \Sigma^T \Sigma V^T
$$
and
$$
A A^T = U \Sigma \Sigma^T U^T
$$
Thus PCA is equivalent to performing SVD on $A$.

---
### Final Conclusion

Instead of computing eigen-decomposition of
$$
C \in \mathbb{R}^{d \times d}
$$
one computes eigen-decomposition of
$$
\frac{1}{n} A A^T \in \mathbb{R}^{n \times n}
$$
This reduces computational cost when
$$
d \gg n
$$
and yields the same principal components.

---
`***********************************************************************************`

---
