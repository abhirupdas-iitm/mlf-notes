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
## Lecture 2
### Example of Singular Value Decomposition

### Problem Setup

Given the matrix
$$
A = \begin{pmatrix}
\sqrt{2} & 1 \\
0 & \sqrt{2}
\end{pmatrix}
$$
Goal: Find the Singular Value Decomposition of $A$.

---
### Step 1: Check Diagonalizability

#### Eigenvalues of $A$
Solve $\det A - \lambda I = 0$.
Eigenvalue:
$$
\lambda = \sqrt{2}
$$
with algebraic multiplicity $2$.
Compute
$$
A - \sqrt{2} I =
\begin{pmatrix}
0 & 1 \\
0 & 0
\end{pmatrix}
$$
Solving
$$
A - \sqrt{2} I
\begin{pmatrix}
x_1 \\
x_2
\end{pmatrix}
=
0
$$
gives
$$
x_2 = 0
$$
Thus eigenvectors are multiples of
$$
\begin{pmatrix}
1 \\
0
\end{pmatrix}
$$
Only one linearly independent eigenvector.
#### Conclusion

$A$ is not diagonalizable.
Therefore proceed with SVD.

---
### Step 2: Compute $A^T A$
$$
A^T =
\begin{pmatrix}
\sqrt{2} & 0 \\
1 & \sqrt{2}
\end{pmatrix}
$$
Then
$$
A^T A =
\begin{pmatrix}
2 & \sqrt{2} \\
\sqrt{2} & 3
\end{pmatrix}
$$
This is real symmetric.

---
### Step 3: Eigenvalues of $A^T A$

Solve
$$
\det
\begin{pmatrix}
2 - \lambda & \sqrt{2} \\
\sqrt{2} & 3 - \lambda
\end{pmatrix}
= 0
$$
This gives
$$
\lambda_1 = 4, \quad \lambda_2 = 1
$$
---
### Step 4: Singular Values

Singular values are
$$
\sigma_i = \sqrt{\lambda_i}
$$
Thus
$$
\sigma_1 = 2, \quad \sigma_2 = 1
$$
So
$$
\Sigma =
\begin{pmatrix}
2 & 0 \\
0 & 1
\end{pmatrix}
$$
---
### Step 5: Eigenvectors of $A^T A$

#### For $\lambda_1 = 4$
Solve
$$
A^T A - 4I =
\begin{pmatrix}
-2 & \sqrt{2} \\
\sqrt{2} & -1
\end{pmatrix}
$$
Eigenvector:
$$
\begin{pmatrix}
1 \\
\sqrt{2}
\end{pmatrix}
$$
Normalize:
Length is $\sqrt{3}$.
$$
x_1 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
1 \\
\sqrt{2}
\end{pmatrix}
$$
---
#### For $\lambda_2 = 1$

Solve
$$
A^T A - I =
\begin{pmatrix}
1 & \sqrt{2} \\
\sqrt{2} & 2
\end{pmatrix}
$$
Eigenvector:
$$
\begin{pmatrix}
\sqrt{2} \\
-1
\end{pmatrix}
$$
Normalize:
Length is $\sqrt{3}$.
$$
x_2 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
\sqrt{2} \\
-1
\end{pmatrix}
$$
---
### Step 6: Construct $Q_2$
$$
Q_2 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
1 & \sqrt{2} \\
\sqrt{2} & -1
\end{pmatrix}
$$
Columns are orthonormal eigenvectors of $A^T A$.

---
### Step 7: Compute Left Singular Vectors

Using
$$
\sigma_i y_i = A x_i
$$
#### Compute $y_1$
$$
A x_1 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
2\sqrt{2} \\
2
\end{pmatrix}
$$
Divide by $\sigma_1 = 2$:
$$
y_1 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
\sqrt{2} \\
1
\end{pmatrix}
$$
---
#### Compute $y_2$
$$
A x_2 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
\sqrt{2} \\
- \sqrt{2}
\end{pmatrix}
$$
Divide by $\sigma_2 = 1$:
$$
y_2 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
\sqrt{2} \\
- \sqrt{2}
\end{pmatrix}
$$
Normalize:
$$
y_2 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
1 \\
- \sqrt{2}
\end{pmatrix}
$$
---
### Step 8: Construct $Q_1$
$$
Q_1 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
\sqrt{2} & 1 \\
1 & -\sqrt{2}
\end{pmatrix}
$$
Columns are orthonormal.

---
### Final SVD
$$
A = Q_1 \Sigma Q_2^T
$$
Where
$$
Q_1 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
\sqrt{2} & 1 \\
1 & -\sqrt{2}
\end{pmatrix}
$$
$$
\Sigma =
\begin{pmatrix}
2 & 0 \\
0 & 1
\end{pmatrix}
$$
$$
Q_2 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
1 & \sqrt{2} \\
\sqrt{2} & -1
\end{pmatrix}
$$
---
### Important Observations

1. $A$ is not diagonalizable.
2. $A^T A$ is symmetric and diagonalizable.
3. Singular values are square roots of eigenvalues of $A^T A$.
4. Columns of $Q_2$ are eigenvectors of $A^T A$.
5. Columns of $Q_1$ are eigenvectors of $A A^T$.
6. SVD exists even when $A$ is not diagonalizable.

---
`***********************************************************************************`

---
## Lecture 3 
### Positive Definiteness and Quadratic Forms

### 1. Motivation via Quadratic Functions
Consider the quadratic function
$$
f(x,y) = 2x^2 + 4xy + y^2
$$
---
### 2. Stationary Point

A stationary point occurs when first derivatives vanish.
Compute partial derivatives:
$$
\frac{\partial f}{\partial x} = 4x + 4y
$$
$$
\frac{\partial f}{\partial y} = 4x + 2y
$$
At $(0,0)$:
$$
\frac{\partial f}{\partial x} = 0
$$
$$
\frac{\partial f}{\partial y} = 0
$$
Thus $(0,0)$ is a stationary point.

---
### 3. Nature of Stationary Point

Second derivatives:
$$
\frac{\partial^2 f}{\partial x^2} = 4
$$
$$
\frac{\partial^2 f}{\partial x \partial y} = 4
$$
$$
\frac{\partial^2 f}{\partial y^2} = 2
$$
The origin is a minimum for this function.

---
### 4. General Quadratic Form in Two Variables

Consider
$$
f(x,y) = ax^2 + 2bxy + cy^2
$$
Observation:
Every quadratic function has a stationary point at $(0,0)$.

---
### 5. Definition: Positive Definite Function

A function $f$ is positive definite if
$$
f(0,0) = 0
$$
and
$$
f(x,y) > 0 \quad \text{for all } (x,y) \ne (0,0)
$$
---
### 6. Necessary Conditions

Evaluate at $(1,0)$:
$$
f(1,0) = a
$$
If $f$ is positive definite:
$$
a > 0
$$
Evaluate at $(0,1)$:
$$
f(0,1) = c
$$
Thus:
$$
c > 0
$$
---
### 7. Completing the Square

Rewrite
$$
ax^2 + 2bxy + cy^2
$$
as
$$
a \left(x + \frac{b}{a} y \right)^2 + \left(c - \frac{b^2}{a}\right) y^2
$$
For positive definiteness:
1. $a > 0$
2. $c - \frac{b^2}{a} > 0$

Equivalent to:
$$
ac - b^2 > 0
$$
---
### 8. Necessary and Sufficient Condition

The quadratic form
$$
f(x,y) = ax^2 + 2bxy + cy^2
$$
is positive definite if and only if
$$
a > 0
$$
and
$$
ac - b^2 > 0
$$
---
### 9. Other Cases

If
$$
ac = b^2
$$
then $f$ is positive semidefinite.
If
$$
ac < b^2
$$
then $(0,0)$ is a saddle point.

---
### 10. Matrix Representation

Let
$$
v =
\begin{pmatrix}
x \\
y
\end{pmatrix}
$$
and
$$
A =
\begin{pmatrix}
a & b \\
b & c
\end{pmatrix}
$$
Then
$$
f(x,y) = v^T A v
$$
---
### 11. General Quadratic Form

For $v = (x_1, \dots, x_n)^T$ and matrix $A = (a_{ij})$,
$$
v^T A v = \sum_{i=1}^n \sum_{j=1}^n a_{ij} x_i x_j
$$
Explicitly,
$$
f(v) = a_{11}x_1^2 + 2a_{12}x_1x_2 + \dots + a_{nn}x_n^2
$$
At $v = 0$:
$$
f(v) = 0
$$
---
### 12. Examples

#### Example 1
$$
f(x,y) = 2x^2 + 4xy + y^2
$$
Here
$$
a = 2, \quad b = 2, \quad c = 1
$$
$$
ac = 2, \quad b^2 = 4
$$
Since
$$
ac < b^2
$$
Origin is a saddle point.

---
#### Example 2
$$
f(x,y) = 2xy
$$
Matrix:
$$
A =
\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}
$$
Saddle at origin.

---
#### Example 3
$$
f(x_1,x_2,x_3) =
2x_1^2 - 2x_1x_2 + 2x_2^2
- 2x_2x_3 + 2x_3^2
$$
Matrix form:
$$
A =
\begin{pmatrix}
2 & -1 & 0 \\
-1 & 2 & -1 \\
0 & -1 & 2
\end{pmatrix}
$$
At origin the function has a minimum.

---
### 13. Connection to Linear Algebra

Quadratic form:
$$
f(v) = v^T A v
$$
Positive definiteness of $f$ relates to properties of matrix $A$.
This leads to the definition of positive definite matrices.

---
`***********************************************************************************`

---
