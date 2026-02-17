## Lecture 1
### Complex Vector Spaces and Hermitian Matrices

### 1. Complex Vector Space

#### Definition: Complex Euclidean Space
Denote by $C^n$ the complex counterpart of $R^n$.
An element $x \in C^n$ is written as
$$
x = (x_1, x_2, \dots, x_n)
$$
where each $x_i \in C$ for $i = 1, \dots, n$.

---
### 2. Complex Numbers

Let $z = a + ib$, where $a,b \in R$.
#### Addition
$$
(a + ib) + (c + id) = (a + c) + i(b + d)
$$
#### Multiplication
$$
(a + ib)(c + id) = (ac - bd) + i(bc + ad)
$$
#### Complex Conjugate

The complex conjugate of $z = a + ib$ is
$$
\bar{z} = a - ib
$$
In polar form,
$$
a + ib = r e^{i\theta}
$$
then
$$
\bar{z} = r e^{-i\theta}
$$
where
$$
r^2 = a^2 + b^2
$$
---
### 3. Linear Combinations in $C^n$

Given vectors $x_1, \dots, x_k \in C^n$, a linear combination is
$$
c_1 x_1 + c_2 x_2 + \dots + c_k x_k
$$
where scalars $c_1, \dots, c_k \in C$.
A linear dependence relation is
$$
c_1 x_1 + \dots + c_k x_k = 0
$$
---
### 4. Inner Product in $R^n$

In real space,
$$
x \cdot y = x^T y
$$
and length is
$$
\|x\|^2 = x^T x
$$
---
### 5. Failure of Naive Definition in $C^n$

If we define
$$
\|x\|^2 = x^T x
$$
then for
$$
x = (1, i)
$$
we get
$$
1^2 + i^2 = 1 - 1 = 0
$$
which contradicts geometric intuition.

---
### 6. Inner Product in $C^n$

#### Definition

For $x, y \in C^n$, define
$$
x \cdot y = \bar{x}^T y
$$
Explicitly,
$$
x \cdot y = \sum_{i=1}^n \bar{x}_i y_i
$$
Equivalently,
$$
x \cdot y = x^* y
$$
where $x^*$ denotes conjugate transpose.

---
### 7. Norm in $C^n$

#### Definition

For $x \in C^n$,
$$
\|x\| = \sqrt{\bar{x}^T x}
$$
Example:
For $x = (1, i)$,
$$
\|x\|^2 = \bar{1} \cdot 1 + \bar{i} \cdot i
$$
$$
= 1 + (-i)(i)
$$
$$
= 1 + 1 = 2
$$
Thus,
$$
\|x\| = \sqrt{2}
$$
Property:
$$
\|x\| = 0 \iff x = 0
$$
---
### 8. Properties of Complex Inner Product

Let $c \in C$.
1.
$$
x \cdot y = \overline{y \cdot x}
$$
2.
$$
x \cdot (c y) = c (x \cdot y)
$$
3.
$$
(c x) \cdot y = \bar{c} (x \cdot y)
$$
---
### 9. Conjugate Transpose

#### Definition

For a matrix $A$, its conjugate transpose is
$$
A^* = \bar{A}^T
$$
Equivalently, transpose first and then conjugate.

---
#### Example

If
$$
A =
\begin{pmatrix}
1+i & 3-2i \\
2-4i & i
\end{pmatrix}
$$
Then
$$
\bar{A} =
\begin{pmatrix}
1-i & 3+2i \\
2+4i & -i
\end{pmatrix}
$$
and
$$
A^* = \bar{A}^T
$$
---
#### Real Case

If $A$ is real,
$$
A^* = A^T
$$
---
### 10. Properties of Conjugate Transpose

1.
$$
(A^*)^* = A
$$
2.
$$
(AB)^* = B^* A^*
$$
Real case equivalents:
$$
(A^T)^T = A
$$
$$
(AB)^T = B^T A^T
$$
---
### 11. Hermitian Matrix

#### Definition

A matrix $A$ is Hermitian if
$$
A^* = A
$$
Hermitian matrices are the complex analogue of symmetric matrices.
Real symmetric condition:
$$
A^T = A
$$
Complex Hermitian condition:
$$
A^* = A
$$
---
### Summary

1. Defined complex vector space $C^n$.
2. Introduced complex conjugation.
3. Defined inner product using conjugation.
4. Defined norm in $C^n$.
5. Introduced conjugate transpose.
6. Defined Hermitian matrices.
7. Established foundational tools for spectral theorem in complex spaces.

---
`***********************************************************************************`

---

## Lecture 2 
### Properties of Hermitian Matrices

## 1. Hermitian Matrix

#### Definition

A matrix $A \in C^{n \times n}$ is Hermitian if
$$
A^* = A
$$
where $A^*$ denotes the conjugate transpose of $A$.

---
#### Example
Consider
$$
A =
\begin{pmatrix}
2 & 3 - 3i \\
3 + 3i & 5
\end{pmatrix}
$$
Compute conjugate:
$$
\bar{A} =
\begin{pmatrix}
2 & 3 + 3i \\
3 - 3i & 5
\end{pmatrix}
$$
Transpose:
$$
A^* =
\begin{pmatrix}
2 & 3 - 3i \\
3 + 3i & 5
\end{pmatrix}
$$
Thus
$$
A^* = A
$$
Hence $A$ is Hermitian.

---
#### Observation

Diagonal entries of a Hermitian matrix are real.
If $A^* = A$, then
$$
a_{ii} = \overline{a_{ii}}
$$
which implies $a_{ii}$ is real.

---
### 2. Property 1: Eigenvalues of Hermitian Matrices Are Real

#### Theorem

If $A$ is Hermitian, then every eigenvalue of $A$ is real.

---
#### Example

For
$$
A =
\begin{pmatrix}
2 & 3 - 3i \\
3 + 3i & 5
\end{pmatrix}
$$
Compute characteristic polynomial:
$$
\det A - \lambda I =
\begin{vmatrix}
2 - \lambda & 3 - 3i \\
3 + 3i & 5 - \lambda
\end{vmatrix}
$$
$$
= (2 - \lambda)(5 - \lambda) - (3 - 3i)(3 + 3i)
$$
$$
= (2 - \lambda)(5 - \lambda) - |3 - 3i|^2
$$
$$
= (2 - \lambda)(5 - \lambda) - 18
$$
$$
= \lambda^2 - 7\lambda - 8
$$
$$
= (\lambda - 8)(\lambda + 1)
$$
Eigenvalues:
$$
\lambda_1 = 8, \quad \lambda_2 = -1
$$
Both real.

---
#### Proof

Let
$$
A x = \lambda x, \quad x \ne 0
$$
Take conjugate transpose:
$$
(Ax)^* = (\lambda x)^*
$$
Using properties:
$$
x^* A^* = \bar{\lambda} x^*
$$
Since $A$ is Hermitian:
$$
A^* = A
$$
Multiply by $x$:
$$
x^* A x = \bar{\lambda} x^* x
$$
But from eigen equation:
$$
x^* A x = x^* \lambda x = \lambda x^* x
$$
Thus
$$
\lambda x^* x = \bar{\lambda} x^* x
$$
Since $x \ne 0$, we have $x^* x \ne 0$.
Therefore
$$
\lambda = \bar{\lambda}
$$
Hence $\lambda$ is real.

---
### 3. Property 2: Orthogonality of Eigenvectors

#### Theorem

Let $A$ be Hermitian.
Suppose
$$
A x = \lambda_1 x
$$
$$
A y = \lambda_2 y
$$
with
$$
\lambda_1 \ne \lambda_2
$$
Then
$$
x^* y = 0
$$
---
#### Example

Eigenvalues: $8$ and $-1$.
Eigenvector for $8$:
Solve
$$
A - 8I =
\begin{pmatrix}
-6 & 3 - 3i \\
3 + 3i & -3
\end{pmatrix}
$$
One eigenvector:
$$
x =
\begin{pmatrix}
1 \\
1 + i
\end{pmatrix}
$$
Eigenvector for $-1$:
Solve
$$
A + I =
\begin{pmatrix}
3 & 3 - 3i \\
3 + 3i & 6
\end{pmatrix}
$$
One eigenvector:
$$
y =
\begin{pmatrix}
1 - i \\
-1
\end{pmatrix}
$$
Compute inner product:
$$
x^* y =
\begin{pmatrix}
1 & 1 - i
\end{pmatrix}
\begin{pmatrix}
1 - i \\
-1
\end{pmatrix}
= 0
$$
Thus eigenvectors are orthogonal.

---
#### Proof

We have
$$
A x = \lambda_1 x
$$
$$
A y = \lambda_2 y
$$
Compute
$$
x^* A y
$$
Using second equation:
$$
x^* A y = \lambda_2 x^* y
$$
Using Hermitian property:
$$
x^* A y = x^* A^* y = (Ax)^* y
$$
Using first equation:
$$
(Ax)^* y = (\lambda_1 x)^* y
$$
$$
= \bar{\lambda_1} x^* y
$$
From Property 1, $\lambda_1$ is real, hence
$$
\bar{\lambda_1} = \lambda_1
$$
Thus
$$
x^* A y = \lambda_1 x^* y
$$
Equating both expressions:
$$
\lambda_2 x^* y = \lambda_1 x^* y
$$
Hence
$$
(\lambda_1 - \lambda_2) x^* y = 0
$$
Since $\lambda_1 \ne \lambda_2$,
$$
x^* y = 0
$$
---
### 4. Relation to Real Symmetric Matrices

If $A$ is real and symmetric,
$$
A^T = A
$$
Since conjugation has no effect on real numbers,
$$
A^* = A^T
$$
Thus every real symmetric matrix is Hermitian.

---
### 5. Diagonalizability with Distinct Eigenvalues

If an $n \times n$ Hermitian matrix has $n$ distinct eigenvalues:
From Property 2, eigenvectors are orthogonal.
Orthogonal vectors are linearly independent.
Hence we obtain $n$ linearly independent eigenvectors.
Therefore $A$ is diagonalizable.

---
#### Diagonalization Structure

Let $P$ be matrix whose columns are eigenvectors.
Let $D$ be diagonal matrix of eigenvalues.
Then
$$
A = P D P^{-1}
$$
---
#### Example Diagonalization

For the example:
Eigenvalues: $8$, $-1$
Eigenvectors:
$$
P =
\begin{pmatrix}
1 & 1 - i \\
1 + i & -1
\end{pmatrix}
$$
$$
D =
\begin{pmatrix}
8 & 0 \\
0 & -1
\end{pmatrix}
$$
Thus
$$
A = P D P^{-1}
$$
---
### 6. Key Conclusions

1. Eigenvalues of Hermitian matrices are real.
2. Eigenvectors corresponding to distinct eigenvalues are orthogonal.
3. With distinct eigenvalues, Hermitian matrices are diagonalizable.
4. Real symmetric matrices are special cases of Hermitian matrices.

---
`***********************************************************************************`

---
