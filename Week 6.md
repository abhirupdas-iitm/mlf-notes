## Lecture 1 
### Singular Value Decomposition

### 1. Recap: Spectral Theorem

Let $A \in R^{n \times n}$ be real symmetric.
Then:
1. All eigenvalues of $A$ are real.
2. $A$ is orthogonally diagonalizable.

There exists orthogonal $Q$ such that
$$
Q^T A Q = \Lambda
$$
where
- $\Lambda$ is diagonal with eigenvalues $\lambda_1, \dots, \lambda_n$.
- Columns of $Q$ are orthonormal eigenvectors $x_1, \dots, x_n$.
- $Q^T Q = I$.

Equivalently,
$$
A = Q \Lambda Q^T
$$
---
### 2. Motivation for SVD

Eigen decomposition requires:
- Square matrix
- Symmetric structure
However:
Any real $m \times n$ matrix can be decomposed, even if rectangular.
This is the Singular Value Decomposition.

---
### 3. Singular Value Decomposition

#### Theorem
For any real matrix $A \in R^{m \times n}$,
$$
A = Q_1 \Sigma Q_2^T
$$
where:
- $Q_1 \in R^{m \times m}$ is orthogonal
- $Q_2 \in R^{n \times n}$ is orthogonal
- $\Sigma \in R^{m \times n}$ has form
$$
\Sigma =
\begin{pmatrix}
D & 0 \\
0 & 0
\end{pmatrix}
$$
where
$$
D = \operatorname{diag}(\sigma_1, \dots, \sigma_r)
$$
with $\sigma_i > 0$.

---
### 4. Proof of SVD

#### Step 1: Consider $A^T A$

Let
$$
A \in R^{m \times n}
$$
Then
$$
A^T A \in R^{n \times n}
$$
and $A^T A$ is symmetric.
By spectral theorem:
There exists orthonormal eigenvectors $x_1, \dots, x_n$ such that
$$
A^T A x_i = \lambda_i x_i
$$
with
$$
x_i^T x_j = 0 \text{ if } i \ne j
$$
$$
\|x_i\| = 1
$$
---
#### Step 2: Non-negativity of Eigenvalues

Compute
$$
x_i^T A^T A x_i = \lambda_i x_i^T x_i
$$
Since $\|x_i\| = 1$,
$$
x_i^T A^T A x_i = \lambda_i
$$
But also
$$
x_i^T A^T A x_i = (A x_i)^T (A x_i) = \|A x_i\|^2
$$
Thus
$$
\lambda_i = \|A x_i\|^2 \ge 0
$$
Hence eigenvalues of $A^T A$ are non-negative.

---
#### Step 3: Order Eigenvalues

Arrange:
$$
\lambda_1 \ge \lambda_2 \ge \dots \ge \lambda_r > 0
$$
$$
\lambda_{r+1} = \dots = \lambda_n = 0
$$
Define singular values:
$$
\sigma_i = \sqrt{\lambda_i}
$$
for $i = 1, \dots, r$.

---
### 5. Construct Left Singular Vectors

Define
$$
y_i = \frac{1}{\sigma_i} A x_i
$$
for $i = 1, \dots, r$.

---
#### Step 5.1: Norm of $y_i$
$$
\|y_i\| = \frac{1}{\sigma_i} \|A x_i\|
$$
But
$$
\|A x_i\|^2 = \lambda_i
$$
Thus
$$
\|y_i\| = \frac{\sqrt{\lambda_i}}{\sigma_i} = 1
$$
---
#### Step 5.2: Orthogonality

For $i \ne j$:
$$
y_i^T y_j = \frac{1}{\sigma_i \sigma_j} (A x_i)^T (A x_j)
$$
$$
= \frac{1}{\sigma_i \sigma_j} x_i^T A^T A x_j
$$
$$
= \frac{\lambda_j}{\sigma_i \sigma_j} x_i^T x_j
$$
Since $x_i^T x_j = 0$,
$$
y_i^T y_j = 0
$$
Thus $y_1, \dots, y_r$ are orthonormal.

---
#### Step 6: Extend to Basis

Extend $\{y_1, \dots, y_r\}$ to orthonormal basis of $R^m$:
$$
\{y_1, \dots, y_m\}
$$
---
### 6. Define Orthogonal Matrices

Define
$$
Q_1 = \{y_1, \dots, y_m\}
$$
$$
Q_2 = \{x_1, \dots, x_n\}
$$
Both are orthogonal.

---
### 7. Compute $\Sigma$

Compute
$$
Q_1^T A Q_2
$$
Entry in position $i,j$:
$$
y_i^T A x_j
$$
---
#### Case 1: $j \le r$

Since
$$
A x_j = \sigma_j y_j
$$
we get
$$
y_i^T A x_j = \sigma_j y_i^T y_j
$$
Thus
$$
y_i^T A x_j =
\begin{cases}
\sigma_j & i = j \\
0 & i \ne j
\end{cases}
$$
---
#### Case 2: $j > r$

Since $\lambda_j = 0$,
$$
A x_j = 0
$$
Hence
$$
y_i^T A x_j = 0
$$
---
#### Final Form

Therefore
$$
Q_1^T A Q_2 = \Sigma
$$
where
$$
\Sigma =
\begin{pmatrix}
\sigma_1 & & & 0 \\
& \ddots & & \\
& & \sigma_r & \\
0 & & & 0
\end{pmatrix}
$$
Thus
$$
A = Q_1 \Sigma Q_2^T
$$
This is the Singular Value Decomposition.

---
### 8. Structural Interpretation

From
$$
A = Q_1 \Sigma Q_2^T
$$
we obtain
$$
A A^T = Q_1 \Sigma \Sigma^T Q_1^T
$$
Thus columns of $Q_1$ are eigenvectors of $A A^T$.
Similarly,
$$
A^T A = Q_2 \Sigma^T \Sigma Q_2^T
$$
Thus columns of $Q_2$ are eigenvectors of $A^T A$.

---
### 9. Key Observations

1. SVD exists for every real $m \times n$ matrix.
2. Singular values are square roots of eigenvalues of $A^T A$.
3. $Q_2$ contains eigenvectors of $A^T A$.
4. $Q_1$ contains eigenvectors of $A A^T$.
5. No symmetry or squareness assumption required.

---
`***********************************************************************************`

---
