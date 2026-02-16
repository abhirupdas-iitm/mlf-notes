## Lecture 1
### Eigenvalues and Eigenvectors

### Motivation from Ordinary Differential Equations

We consider a system of linear ordinary differential equations.
Let $u t \in \mathbb{R}^2$ and suppose
$$
\frac{du}{dt} = A u
$$
with initial condition
$$
u 0 = u_0
$$
where
$$
A = 
\begin{pmatrix}
4 & -5 \\
2 & -3
\end{pmatrix}
$$
To understand this system, we first consider the one-dimensional case.
#### One-Dimensional Case

Suppose
$$
\frac{du}{dt} = a u
$$
We verify that a solution is
$$
u t = e^{a t} u 0
$$
We differentiate:
$$
\frac{d}{dt} \left( e^{a t} u 0 \right) = a e^{a t} u 0 = a u t
$$
Thus the solution satisfies the differential equation.
#### Stability
If $a > 0$, then $e^{a t} \to \infty$ as $t \to \infty$, so the system is unstable.
If $a < 0$, then $e^{a t} \to 0$ as $t \to \infty$, so the system is stable.
#### Two-Dimensional Case

We seek solutions of the form
$$
u t = e^{\lambda t} x
$$
where $x \neq 0$.
Substituting into
$$
\frac{du}{dt} = A u
$$
we obtain
$$
\lambda e^{\lambda t} x = A e^{\lambda t} x
$$
Cancelling $e^{\lambda t}$ gives
$$
A x = \lambda x
$$
This is the eigenvalue equation.

---
### Definition: Eigenvalues and Eigenvectors

Let $A \in \mathbb{R}^{n \times n}$.
We say $\lambda$ is an eigenvalue of $A$ and $x \neq 0$ is an eigenvector if
$$
A x = \lambda x
$$
#### Geometric Interpretation

If $x$ is an eigenvector, then applying $A$ scales $x$ by $\lambda$ without changing its direction.

---
### Special Case: Zero Eigenvalue

If $\lambda = 0$, then
$$
A x = 0
$$
Thus $x$ lies in the null space of $A$.

---
### Example 1: Projection Matrix

Suppose $P$ is a projection matrix onto a plane.
If $x$ lies in the plane, then
$$
P x = x
$$
Thus $\lambda = 1$ is an eigenvalue and every vector in the plane is an eigenvector.
If $x$ is orthogonal to the plane, then
$$
P x = 0
$$
Thus $\lambda = 0$ is another eigenvalue and vectors orthogonal to the plane are eigenvectors.

---
### Example 2: Permutation Matrix

Consider
$$
P =
\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}
$$
We compute:
If $x = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$ then
$$
P x = x
$$
Thus $\lambda = 1$.
If $x = \begin{pmatrix} 1 \\ -1 \end{pmatrix}$ then
$$
P x = -x
$$
Thus $\lambda = -1$.

---
### Characteristic Polynomial

Starting from
$$
A x = \lambda x
$$
we rewrite as
$$
A x - \lambda x = 0
$$
$$
A x - \lambda I x = 0
$$
$$
\left( A - \lambda I \right) x = 0
$$
For non-trivial solutions, we require
$$
\det \left( A - \lambda I \right) = 0
$$
This is called the characteristic polynomial.
If $A$ is $n \times n$, then the characteristic polynomial is degree $n$.
The roots are the eigenvalues.

---
### Finding Eigenvectors

Given an eigenvalue $\lambda$, we solve
$$
\left( A - \lambda I \right) x = 0
$$
Thus $x$ belongs to the null space of $A - \lambda I$.

---
### Example

Let
$$
A =
\begin{pmatrix}
3 & 1 \\
1 & 3
\end{pmatrix}
$$
#### Step 1: Eigenvalues

We compute
$$
\det \left( A - \lambda I \right)
=
\det
\begin{pmatrix}
3 - \lambda & 1 \\
1 & 3 - \lambda
\end{pmatrix}
$$
$$
=
(3 - \lambda)^2 - 1
$$
$$
=
\lambda^2 - 6 \lambda + 8
$$
Solving
$$
\lambda^2 - 6 \lambda + 8 = 0
$$
gives
$$
\lambda_1 = 4, \quad \lambda_2 = 2
$$
#### Step 2: Eigenvectors

For $\lambda = 4$:
$$
A - 4 I =
\begin{pmatrix}
-1 & 1 \\
1 & -1
\end{pmatrix}
$$
Solution:
$$
x =
\begin{pmatrix}
1 \\
1
\end{pmatrix}
$$
For $\lambda = 2$:
$$
A - 2 I =
\begin{pmatrix}
1 & 1 \\
1 & 1
\end{pmatrix}
$$
Solution:
$$
x =
\begin{pmatrix}
1 \\
-1
\end{pmatrix}
$$
---
### Important Observations

If $A$ is symmetric, then all eigenvalues are real.
Eigenvectors corresponding to distinct eigenvalues are linearly independent.
However, not every matrix has a full set of independent eigenvectors.
Example:
$$
A =
\begin{pmatrix}
3 & 1 \\
0 & 3
\end{pmatrix}
$$
Characteristic polynomial:
$$
(3 - \lambda)^2 = 0
$$
Eigenvalue:
$$
\lambda = 3
$$
But solving
$$
A - 3 I =
\begin{pmatrix}
0 & 1 \\
0 & 0
\end{pmatrix}
$$
gives only one independent eigenvector.
Thus the matrix is not diagonalizable.

---
### Summary

To compute eigenvalues:
$$
\det \left( A - \lambda I \right) = 0
$$
To compute eigenvectors:
$$
\left( A - \lambda I \right) x = 0
$$
Eigenvalues determine scaling behavior.
Eigenvectors determine invariant directions.
These concepts are fundamental to diagonalization and further decomposition methods.

---
`***********************************************************************************`

---
## Lecture 2

### Similarity and Diagonalization

### Motivation

In the previous lecture we studied eigenvalues and eigenvectors.  
We now investigate when a matrix can be simplified using them.
The key question:
When can a matrix be transformed into a diagonal matrix?

---
### Definition: Diagonalizable Matrix

Let $A$ be an $n \times n$ matrix.
$A$ is **diagonalizable** if there exists an invertible matrix $S$ such that
$$
S^{-1} A S = \Lambda
$$
where $\Lambda$ is a diagonal matrix.
Equivalently,
$$
A S = S \Lambda
$$
---
### Connection with Eigenvectors

Diagonalizability is tied to having enough linearly independent eigenvectors.
### Main Theorem

Let $A$ be an $n \times n$ matrix.
If $A$ has $n$ linearly independent eigenvectors
$$
x_1, x_2, \dots, x_n
$$
then $A$ is diagonalizable.

---
### Proof Idea

Let eigenvalues corresponding to $x_i$ be $\lambda_i$.
Construct matrix
$$
S = \begin{bmatrix}
| & | & & | \\
x_1 & x_2 & \dots & x_n \\
| & | & & |
\end{bmatrix}
$$
Since eigenvectors are linearly independent,
$$
\text{rank}(S) = n
$$
so $S$ is invertible.
Now compute
$$
A S = A \begin{bmatrix}
x_1 & \dots & x_n
\end{bmatrix}
= \begin{bmatrix}
A x_1 & \dots & A x_n
\end{bmatrix}
$$
Using eigenvalue relation
$$
A x_i = \lambda_i x_i
$$
we get
$$
A S =
\begin{bmatrix}
\lambda_1 x_1 & \dots & \lambda_n x_n
\end{bmatrix}
$$
Factor out:
$$
A S =
\begin{bmatrix}
x_1 & \dots & x_n
\end{bmatrix}
\begin{bmatrix}
\lambda_1 & & 0 \\
& \ddots & \\
0 & & \lambda_n
\end{bmatrix}
$$
Thus
$$
A S = S \Lambda
$$
Multiply by $S^{-1}$:
$$
S^{-1} A S = \Lambda
$$
Hence $A$ is diagonalizable.

---
### Distinct Eigenvalues Imply Independence

#### Claim
If $\lambda_1 \ne \lambda_2$ and
$$
A x_1 = \lambda_1 x_1
$$
$$
A x_2 = \lambda_2 x_2
$$
then $x_1$ and $x_2$ are linearly independent.

---
### Proof

Assume
$$
c_1 x_1 + c_2 x_2 = 0
$$
Apply $A$:
$$
c_1 \lambda_1 x_1 + c_2 \lambda_2 x_2 = 0
$$
Subtract $\lambda_2$ times the original equation:
$$
c_1 (\lambda_1 - \lambda_2) x_1 = 0
$$
Since $\lambda_1 \ne \lambda_2$ and $x_1 \ne 0$,
$$
c_1 = 0
$$
Similarly,
$$
c_2 = 0
$$
Hence independence.

---
### Extension

If $\lambda_1, \dots, \lambda_n$ are distinct, then eigenvectors
$x_1, \dots, x_n$ are linearly independent.
Therefore:
If all eigenvalues of an $n \times n$ matrix are distinct, then it is diagonalizable.

---
### Example

Let
$$
A =
\begin{bmatrix}
1 & 4 \\
2 & 3
\end{bmatrix}
$$
---
#### Step 1: Characteristic Polynomial
$$
\det(A - \lambda I)
=
\begin{vmatrix}
1-\lambda & 4 \\
2 & 3-\lambda
\end{vmatrix}
$$
$$
= (1-\lambda)(3-\lambda) - 8
$$
$$
= \lambda^2 - 4\lambda - 5
$$
Roots:
$$
\lambda_1 = 5
$$
$$
\lambda_2 = -1
$$
Since eigenvalues are distinct, $A$ is diagonalizable.

---
#### Step 2: Eigenvectors

For $\lambda_1 = 5$
$$
A - 5I =
\begin{bmatrix}
-4 & 4 \\
2 & -2
\end{bmatrix}
$$
Eigenvector:
$$
x_1 =
\begin{bmatrix}
1 \\
1
\end{bmatrix}
$$
---
For $\lambda_2 = -1$
$$
A + I =
\begin{bmatrix}
2 & 4 \\
2 & 4
\end{bmatrix}
$$
Eigenvector:
$$
x_2 =
\begin{bmatrix}
-2 \\
1
\end{bmatrix}
$$
---
#### Diagonalization

Construct
$$
S =
\begin{bmatrix}
1 & -2 \\
1 & 1
\end{bmatrix}
$$
$$
\Lambda =
\begin{bmatrix}
5 & 0 \\
0 & -1
\end{bmatrix}
$$
Then
$$
S^{-1} A S = \Lambda
$$
---
### Important Remarks

#### Non-uniqueness of $S$
If $x$ is an eigenvector, then any scalar multiple $c x$ is also an eigenvector.
Therefore $S$ is not unique.
However, eigenvalues on diagonal of $\Lambda$ are fixed.

---
### Powers of a Matrix

If
$$
A x = \lambda x
$$
then
$$
A^2 x = A(\lambda x) = \lambda A x = \lambda^2 x
$$
More generally,
$$
A^k x = \lambda^k x
$$
If
$$
S^{-1} A S = \Lambda
$$
then
$$
S^{-1} A^k S = \Lambda^k
$$
Thus diagonalization simplifies matrix powers.

---
### Non-Diagonalizable Example

Let
$$
A =
\begin{bmatrix}
3 & 1 \\
0 & 3
\end{bmatrix}
$$
Characteristic polynomial:
$$
(3-\lambda)^2
$$
Eigenvalue:
$$
\lambda = 3
$$
Compute
$$
A - 3I =
\begin{bmatrix}
0 & 1 \\
0 & 0
\end{bmatrix}
$$
Null space gives only one independent eigenvector.
Hence:
Matrix does not have two linearly independent eigenvectors.
Therefore it is not diagonalizable.

---
### Key Takeaways

1. A matrix is diagonalizable if it has $n$ linearly independent eigenvectors.
2. Distinct eigenvalues guarantee independence.
3. Diagonalization converts $A$ into
   $S^{-1} A S = \Lambda$.
4. Powers of $A$ become easy:
   $A^k = S \Lambda^k S^{-1}$.
5. Not all matrices are diagonalizable.
6. Real symmetric matrices will later be shown to always be diagonalizable.

---
`***********************************************************************************`

---

