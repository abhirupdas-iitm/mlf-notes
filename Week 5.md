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
`*********************************************************************************`

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
`*********************************************************************************`

---
## Lecture 3
### Unitary Matrices and Their Properties

### 1. Definition of Unitary Matrix

Let $U \in C^{n \times n}$.
#### Definition
$U$ is unitary if
$$
U^* U = I
$$
Equivalently,
$$
U^{-1} = U^*
$$
This is the complex analogue of an orthogonal matrix in $R^n$.

---
### 2. Orthonormal Columns Interpretation

Let
$$
U = \{u_1 \ \dots \ u_n\}
$$
where $u_i$ are the columns of $U$.
Then
$$
u_i^* u_j = 0 \quad \text{for } i \ne j
$$
$$
u_i^* u_i = 1 \quad \text{for all } i
$$
Thus columns of a unitary matrix form an orthonormal set.

---
### 3. Relation to Orthogonal Matrices

In the real case,
$$
Q^T Q = I
$$
implies
$$
Q^{-1} = Q^T
$$
In the complex case,
$$
U^* U = I
$$
implies
$$
U^{-1} = U^*
$$
---
### 4. Examples

#### Example 1
$$
U =
\frac{1}{\sqrt{2}}
\begin{pmatrix}
1 & i \\
i & 1
\end{pmatrix}
$$
Verify:
$$
U^* U = I
$$
---
#### Example 2
$$
U =
\begin{pmatrix}
\cos t & -\sin t \\
\sin t & \cos t
\end{pmatrix}
$$
In the real case, this satisfies
$$
U^T U = I
$$
---
### 5. Property 1: Length Preservation

Let $U$ be unitary.
For any $x, y \in C^n$,
$$
Ux \cdot Uy = x \cdot y
$$
#### Proof
$$
Ux \cdot Uy = (Ux)^* Uy
$$
$$
= x^* U^* U y
$$
Since $U^* U = I$,
$$
= x^* y
$$
Thus
$$
Ux \cdot Uy = x \cdot y
$$
Taking $y = x$,
$$
\|Ux\|^2 = \|x\|^2
$$
Hence
$$
\|Ux\| = \|x\|
$$
Unitary transformations preserve length.

---
### 6. Property 2: Eigenvalues Have Absolute Value 1

#### Theorem

If $\lambda$ is an eigenvalue of a unitary matrix $U$, then
$$
|\lambda| = 1
$$
---
#### Proof

Let
$$
Ux = \lambda x
$$
with $x \ne 0$.
Using length preservation:
$$
\|Ux\| = \|x\|
$$
But
$$
\|Ux\| = \|\lambda x\|
$$
$$
= |\lambda| \|x\|
$$
Thus
$$
|\lambda| \|x\| = \|x\|
$$
Since $\|x\| \ne 0$,
$$
|\lambda| = 1
$$
---
#### Alternative Proof

Compute
$$
Ux \cdot Ux = \lambda x \cdot \lambda x
$$
Left side:
$$
Ux \cdot Ux = x \cdot x
$$
Right side:
$$
\lambda x \cdot \lambda x
= \bar{\lambda} \lambda x \cdot x
$$
Thus
$$
\bar{\lambda} \lambda x \cdot x = x \cdot x
$$
Since $x \cdot x \ne 0$,
$$
\bar{\lambda} \lambda = 1
$$
Hence
$$
|\lambda| = 1
$$
---
### 7. Property 3: Orthogonality of Eigenvectors

Let
$$
Ux = \lambda_1 x
$$
$$
Uy = \lambda_2 y
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
#### Proof

Since $U$ preserves inner products,
$$
x \cdot y = Ux \cdot Uy
$$
Using eigen relations:
$$
Ux \cdot Uy = \lambda_1 x \cdot \lambda_2 y
$$
$$
= \bar{\lambda_1} \lambda_2 x \cdot y
$$
Thus
$$
x \cdot y = \bar{\lambda_1} \lambda_2 x \cdot y
$$
Hence
$$
(\bar{\lambda_1} \lambda_2 - 1) x \cdot y = 0
$$
If
$$
\bar{\lambda_1} \lambda_2 = 1
$$
then multiplying both sides by $\lambda_1$,
$$
\lambda_2 = \lambda_1
$$
since $|\lambda_1| = 1$.
This contradicts $\lambda_1 \ne \lambda_2$.
Therefore
$$
\bar{\lambda_1} \lambda_2 \ne 1
$$
Hence
$$
x \cdot y = 0
$$
---
### 8. Preview: Spectral Theorem

For a Hermitian matrix $A$, there exists a unitary matrix $U$ such that
$$
A = U \Lambda U^*
$$
where $\Lambda$ is diagonal with eigenvalues of $A$.

---
### 9. Real Symmetric Case

If $A$ is real symmetric, then there exists an orthogonal matrix $Q$ such that
$$
A = Q \Lambda Q^T
$$
This is the spectral theorem in the real case.

---
`*********************************************************************************`

---
## Lecture 4
### Schur Theorem and Upper Triangularization

### 1. Recap of Definitions

#### Conjugate Transpose

For $A \in C^{n \times n}$,
$$
A^* = \bar{A}^T
$$
---
#### Hermitian Matrix

$A$ is Hermitian if
$$
A^* = A
$$
---
#### Unitary Matrix

$U$ is unitary if
$$
U^* U = I
$$
Equivalently,
$$
U^{-1} = U^*
$$
---
#### Unitary Diagonalization

A matrix $A$ is unitarily diagonalizable if there exists a unitary matrix $U$ such that
$$
A = U \Lambda U^*
$$
where $\Lambda$ is diagonal.

---
### 2. Goal

Prove that Hermitian matrices are unitarily diagonalizable.
#### Strategy

1. Prove that any $n \times n$ complex matrix is unitarily similar to an upper triangular matrix.
2. Use this result to prove Hermitian matrices are unitarily diagonalizable.

---
### 3. Schur Theorem

#### Theorem

For any $A \in C^{n \times n}$, there exists a unitary matrix $U$ such that
$$
A = U T U^*
$$
where $T$ is upper triangular.
Equivalently,
$$
U^* A U = T
$$
---
### 4. Proof for $n = 3$

Let $A \in C^{3 \times 3}$.
#### Step 1: Choose Eigenvalue
Let
$$
p \lambda
$$
be the characteristic polynomial of $A$.
Let $\lambda_1$ be a root.
Let $z_1$ be corresponding eigenvector:
$$
A z_1 = \lambda_1 z_1
$$
---
#### Step 2: Extend to Orthonormal Basis

Extend $z_1$ to a basis and apply Gram Schmidt to obtain orthonormal basis:
$$
\{ z_1, u, v \}
$$
Construct
$$
U_1 = \{ z_1 \ u \ v \}
$$
Then $U_1$ is unitary.

---
#### Step 3: Compute $U_1^* A U_1$

Since
$$
A z_1 = \lambda_1 z_1
$$
we obtain
$$
U_1^* A U_1 =
\begin{pmatrix}
\lambda_1 & * & * \\
0 & & \\
0 & & B
\end{pmatrix}
$$
where $B$ is $2 \times 2$.
Reason:
$$
z_1^* A z_1 = \lambda_1
$$
and orthogonality implies lower entries of first column are zero.

---
#### Step 4: Apply Procedure to $B$

Let $\lambda_2$ be eigenvalue of $B$.
Construct unitary $P$ such that
$$
P^* B P =
\begin{pmatrix}
\lambda_2 & * \\
0 & \lambda_3
\end{pmatrix}
$$
---
#### Step 5: Embed $P$ into $3 \times 3$

Define
$$
U_2 =
\begin{pmatrix}
1 & 0 & 0 \\
0 & & \\
0 & & P
\end{pmatrix}
$$
Then $U_2$ is unitary.

---
#### Step 6: Combine Transformations

Compute
$$
U_2^* U_1^* A U_1 U_2
$$
This equals an upper triangular matrix $T$.
Let
$$
U = U_1 U_2
$$
Then $U$ is unitary and
$$
U^* A U = T
$$
Thus
$$
A = U T U^*
$$
---
### 5. General Case

The same procedure extends inductively to any $n$.
At each step:
1. Extract one eigenvalue.
2. Reduce dimension by 1.
3. Continue recursively.

Thus any complex matrix is unitarily similar to an upper triangular matrix.

---
### 6. Example

Consider
$$
A =
\begin{pmatrix}
5 & 8 & 16 \\
5 & 0 & 9 \\
-3 & -5 & -10
\end{pmatrix}
$$
---
#### Step 1: Characteristic Polynomial

Eigenvalues:
$$
\lambda_1 = 1
$$
$$
\lambda_2 = -3
$$
with $-3$ repeated.

---
#### Step 2: Eigenvector for $\lambda_1$

One eigenvector:
$$
z_1 =
\begin{pmatrix}
-2 \\
-1 \\
1
\end{pmatrix}
$$
---
#### Step 3: Construct Orthonormal Basis

After Gram Schmidt, obtain
$$
U_1 =
\begin{pmatrix}
-2 / \sqrt{6} & 1 / \sqrt{3} & 0 \\
-1 / \sqrt{6} & -1 / \sqrt{3} & 1 / \sqrt{2} \\
1 / \sqrt{6} & 1 / \sqrt{3} & 1 / \sqrt{2}
\end{pmatrix}
$$
---
#### Step 4: Compute $U_1^T A U_1$

Result:
$$
U_1^T A U_1 =
\begin{pmatrix}
1 & -8 \sqrt{2} & -12 \sqrt{3} \\
0 & -3 & 0 \\
0 & \sqrt{6} & -3
\end{pmatrix}
$$
Extract
$$
B =
\begin{pmatrix}
-3 & 0 \\
\sqrt{6} & -3
\end{pmatrix}
$$
---
#### Step 5: Diagonalize $B$ to Upper Triangular Form

Choose permutation matrix
$$
P =
\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}
$$
Then
$$
P^T B P =
\begin{pmatrix}
-3 & \sqrt{6} \\
0 & -3
\end{pmatrix}
$$
---
#### Step 6: Construct $U_2$

Embed $P$:
$$
U_2 =
\begin{pmatrix}
1 & 0 & 0 \\
0 & 0 & 1 \\
0 & 1 & 0
\end{pmatrix}
$$
---
#### Step 7: Final Result

Let
$$
U = U_1 U_2
$$
Then
$$
U^T A U =
\begin{pmatrix}
1 & -8 \sqrt{2} & -12 \sqrt{3} \\
0 & -3 & \sqrt{6} \\
0 & 0 & -3
\end{pmatrix}
$$
This is upper triangular.

---
### 7. Key Observations

1. Any complex matrix can be unitarily upper triangularised.
2. Repeated eigenvalues may prevent diagonalization.
3. Distinct eigenvalues guarantee diagonal form.
4. This theorem enables diagonalization of Hermitian matrices in the next step.

---
`*********************************************************************************`

---
## Lecture 5
### Spectral Theorem for Hermitian Matrices

### 1. Spectral Theorem

#### Theorem

If $A \in C^{n \times n}$ is Hermitian, then $A$ is unitarily diagonalizable.
That is, there exists a unitary matrix $U$ such that
$$
U^* A U = D
$$
where $D$ is a diagonal matrix with real entries.
This implication is one directional:
Hermitian implies unitarily diagonalizable.

---
### 2. Proof Using Schur Theorem

From Schur theorem, for any complex matrix $A$, there exists a unitary matrix $U$ such that
$$
U^* A U = T
$$
where $T$ is upper triangular.
Since $A$ is Hermitian,
$$
A^* = A
$$
Take conjugate transpose of both sides:
$$
T^* = U^* A^* U
$$
Using $A^* = A$,
$$
T^* = U^* A U
$$
Thus
$$
T^* = T
$$
Now observe:
- $T$ is upper triangular.
- $T^*$ is lower triangular.

If an upper triangular matrix equals its conjugate transpose, then it must be diagonal.
Therefore
$$
T \text{ is diagonal}
$$
Hence
$$
U^* A U = D
$$
where $D$ is diagonal.

---
#### Real Diagonal Entries

Since
$$
T = T^*
$$
consider diagonal entries:
$$
T_{ii} = \overline{T_{ii}}
$$
Thus each diagonal entry is real.
Therefore
$$
U^* A U = D
$$
where $D$ is diagonal with real entries.
This completes the proof.

---
### 3. Example: Hermitian Matrix

Consider
$$
A =
\begin{pmatrix}
2 & 1 - i \\
1 + i & 3
\end{pmatrix}
$$
Check:
$$
A^* = A
$$
---
#### Characteristic Polynomial
$$
p \lambda = \det A - \lambda I
$$
$$
= (\lambda - 1)(\lambda - 4)
$$
Eigenvalues:
$$
\lambda_1 = 1
$$
$$
\lambda_2 = 4
$$
---
#### Eigenvectors

For $\lambda_1 = 1$:
$$
z_1 =
\begin{pmatrix}
-1 + i \\
1
\end{pmatrix}
$$
For $\lambda_2 = 4$:
$$
z_2 =
\begin{pmatrix}
1 - i \\
2
\end{pmatrix}
$$
Orthogonality:
$$
z_1^* z_2 = 0
$$
---
#### Normalize

Compute norms and define
$$
u_1 =
\frac{1}{\sqrt{3}}
\begin{pmatrix}
-1 + i \\
1
\end{pmatrix}
$$
$$
u_2 =
\frac{1}{\sqrt{6}}
\begin{pmatrix}
1 - i \\
2
\end{pmatrix}
$$
Construct
$$
U = \{ u_1 \ u_2 \}
$$
Then
$$
U^* A U =
\begin{pmatrix}
1 & 0 \\
0 & 4
\end{pmatrix}
$$
---
### 4. Corollary: Real Symmetric Case

If $A$ is real symmetric, then $A$ is Hermitian.
Thus there exists unitary $U$ such that
$$
U^* A U = D
$$
Since $A$ is real symmetric:
- Eigenvalues are real.
- Eigenvectors can be chosen real.

Thus $U$ can be taken real.
Hence
$$
U^T A U = D
$$
with
$$
U^T U = I
$$
Therefore a real symmetric matrix is orthogonally diagonalizable.
This is the spectral theorem for real symmetric matrices.

---
### 5. Converse Is False

Hermitian implies unitarily diagonalizable.
But unitarily diagonalizable does not imply Hermitian.

---
#### Counterexample

Consider
$$
A =
\begin{pmatrix}
0 & -1 \\
1 & 0
\end{pmatrix}
$$
Compute:
$$
A^* \ne A
$$
Thus $A$ is not Hermitian.

---
#### Eigenvalues

Solve
$$
\det A - \lambda I = 0
$$
Eigenvalues:
$$
\lambda_1 = i
$$
$$
\lambda_2 = -i
$$
Distinct eigenvalues imply diagonalizable.

---
#### Eigenvectors

For $\lambda_1 = i$:
$$
z_1 =
\begin{pmatrix}
1 \\
- i
\end{pmatrix}
$$
For $\lambda_2 = -i$:
$$
z_2 =
\begin{pmatrix}
1 \\
i
\end{pmatrix}
$$
Normalize:
$$
u_1 =
\frac{1}{\sqrt{2}}
\begin{pmatrix}
1 \\
- i
\end{pmatrix}
$$
$$
u_2 =
\frac{1}{\sqrt{2}}
\begin{pmatrix}
1 \\
i
\end{pmatrix}
$$
Let
$$
U = \{ u_1 \ u_2 \}
$$
Then
$$
U^* A U =
\begin{pmatrix}
i & 0 \\
0 & -i
\end{pmatrix}
$$
Thus $A$ is unitarily diagonalizable but not Hermitian.

---
### 6. Summary

1. Every Hermitian matrix is unitarily diagonalizable.
2. The diagonal entries are real eigenvalues.
3. Real symmetric matrices are orthogonally diagonalizable.
4. Converse does not hold: unitarily diagonalizable does not imply Hermitian.

---
`*********************************************************************************`

---
