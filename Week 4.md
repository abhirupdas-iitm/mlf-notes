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

