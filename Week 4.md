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
`**********************************************************************************`

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
`**********************************************************************************`

---
## Lecture 3
### Fibonacci Sequence and Diagonalization

### 1. Motivation

We consider the Fibonacci sequence defined by the recurrence
$$
F_{k+2} = F_{k+1} + F_k
$$
with initial conditions
$$
F_0 = 0, \qquad F_1 = 1.
$$
Our objective is to compute large terms such as $F_{100}$ efficiently using linear algebra instead of brute force iteration.

---
### 2. Matrix Formulation of the Recurrence

We define the state vector
$$
u_k =
\begin{pmatrix}
F_{k+1} \\
F_k
\end{pmatrix}.
$$
Then the recurrence becomes
$$
u_{k+1} = A u_k
$$
where
$$
A =
\begin{pmatrix}
1 & 1 \\
1 & 0
\end{pmatrix}.
$$
Indeed,
$$
\begin{pmatrix}
F_{k+2} \\
F_{k+1}
\end{pmatrix}
=
\begin{pmatrix}
1 & 1 \\
1 & 0
\end{pmatrix}
\begin{pmatrix}
F_{k+1} \\
F_k
\end{pmatrix}.
$$
Thus,
$$
u_k = A^k u_0,
$$
where
$$
u_0 =
\begin{pmatrix}
1 \\
0
\end{pmatrix}.
$$
---
### 3. General Diagonalization Strategy

Suppose $A$ is an $n \times n$ matrix with $n$ linearly independent eigenvectors $x_1, \dots, x_n$ and corresponding eigenvalues $\lambda_1, \dots, \lambda_n$.

If
$$
u_0 = c_1 x_1 + \dots + c_n x_n,
$$
then
$$
A u_0 = c_1 \lambda_1 x_1 + \dots + c_n \lambda_n x_n,
$$
and more generally,
$$
A^k u_0 = c_1 \lambda_1^k x_1 + \dots + c_n \lambda_n^k x_n.
$$
Diagonalization converts matrix powers into scalar powers.

---
### 4. Eigenvalues of the Fibonacci Matrix

For
$$
A =
\begin{pmatrix}
1 & 1 \\
1 & 0
\end{pmatrix},
$$
we compute the characteristic polynomial:
$$
\det(A - \lambda I)
=
\begin{vmatrix}
1 - \lambda & 1 \\
1 & -\lambda
\end{vmatrix}
=
\lambda^2 - \lambda - 1.
$$
Thus eigenvalues satisfy
$$
\lambda^2 - \lambda - 1 = 0.
$$
Hence,
$$
\lambda_1 = \frac{1 + \sqrt{5}}{2}, \qquad
\lambda_2 = \frac{1 - \sqrt{5}}{2}.
$$
Since the eigenvalues are distinct, $A$ is diagonalizable.

---
### 5. Eigenvectors

For each eigenvalue $\lambda$, a corresponding eigenvector is
$$
x =
\begin{pmatrix}
\lambda \\
1
\end{pmatrix}.
$$
Thus,
$$
x_1 =
\begin{pmatrix}
\lambda_1 \\
1
\end{pmatrix},
\qquad
x_2 =
\begin{pmatrix}
\lambda_2 \\
1
\end{pmatrix}.
$$
---
### 6. Expressing the Initial Condition

We write
$$
\begin{pmatrix}
1 \\
0
\end{pmatrix}
=
c_1 x_1 + c_2 x_2.
$$
Solving gives
$$
c_1 = \frac{1}{\sqrt{5}}, \qquad
c_2 = -\frac{1}{\sqrt{5}}.
$$
---
### 7. Closed Form Expression

Using
$$
u_k = A^k u_0 = c_1 \lambda_1^k x_1 + c_2 \lambda_2^k x_2,
$$
we obtain
$$
F_k =
\frac{1}{\sqrt{5}} \lambda_1^k
-
\frac{1}{\sqrt{5}} \lambda_2^k.
$$
Substituting eigenvalues:
$$
F_k =
\frac{1}{\sqrt{5}}
\left( \frac{1 + \sqrt{5}}{2} \right)^k
-
\frac{1}{\sqrt{5}}
\left( \frac{1 - \sqrt{5}}{2} \right)^k.
$$
---
### 8. Approximation for Large k

Since
$$
\left| \frac{1 - \sqrt{5}}{2} \right| < 1,
$$
we have
$$
\left( \frac{1 - \sqrt{5}}{2} \right)^k \to 0
$$
as $k \to \infty$.
Thus for large $k$,
$$
F_k \approx
\frac{1}{\sqrt{5}}
\left( \frac{1 + \sqrt{5}}{2} \right)^k.
$$
In particular,
$$
F_{100} \approx
\frac{1}{\sqrt{5}}
\left( \frac{1 + \sqrt{5}}{2} \right)^{100}.
$$
---
### 9. Key Observations

1. The Fibonacci recurrence is linear.
2. Linear recurrences can be written as matrix systems.
3. Diagonalization reduces matrix powers to scalar powers.
4. Distinct eigenvalues guarantee diagonalizability.
5. Large scale behavior is dominated by the largest eigenvalue.

---
### Final Takeaway

Diagonalization solves linear recurrence relations of the form
$$
u_{k+1} = A u_k
$$
by writing
$$
A^k = S \Lambda^k S^{-1}.
$$
Recursive growth becomes exponential growth governed by eigenvalues.

---
`**********************************************************************************`

---
## Lecture 4
### Spectral Theorem for Real Symmetric Matrices

### 1. Spectral Theorem Statement

We consider a real symmetric matrix $A \in \mathbb{R}^{n \times n}$ satisfying
$$
A^T = A.
$$
The spectral theorem for the real case states the following:
If $A$ is real symmetric, then:
1. All eigenvalues of $A$ are real.
2. Eigenvectors corresponding to distinct eigenvalues are linearly independent.
3. $A$ is orthogonally diagonalizable.

---
### 2. Orthogonal Diagonalization

We say that $A$ is orthogonally diagonalizable if there exists an orthogonal matrix $Q$ such that
$$
Q^T Q = I
$$
and
$$
A = Q \Lambda Q^T,
$$
where $\Lambda$ is a diagonal matrix containing the eigenvalues of $A$.
Since $Q^T Q = I$, we have
$$
Q^{-1} = Q^T.
$$
Thus orthogonal diagonalization is a special case of diagonalization:
$$
A = Q \Lambda Q^{-1},
$$
with the additional constraint that $Q$ is orthogonal.

---
### 3. Important Observations

We note that not every real matrix is diagonalizable.
There exist real matrices that do not possess enough linearly independent eigenvectors.
However, every real symmetric matrix:
- Has only real eigenvalues.
- Has a full set of orthonormal eigenvectors.
- Is orthogonally diagonalizable.

Thus symmetry is the crucial structural condition.

---
### 4. Example of Orthogonal Diagonalization

We consider
$$
A =
\begin{pmatrix}
1 & -2 \\
-2 & -2
\end{pmatrix}.
$$
This matrix is real symmetric.
#### Step 1: Eigenvalues

We compute the characteristic polynomial:
$$
\det A - \lambda I
=
\begin{vmatrix}
1 - \lambda & -2 \\
-2 & -2 - \lambda
\end{vmatrix}.
$$
Solving yields eigenvalues
$$
\lambda_1 = -3,
\quad
\lambda_2 = 2.
$$
---
#### Step 2: Eigenvectors

Corresponding eigenvectors are
$$
x_1 =
\begin{pmatrix}
1 \\
2
\end{pmatrix},
\quad
x_2 =
\begin{pmatrix}
-2 \\
1
\end{pmatrix}.
$$
---
#### Step 3: Orthonormalization

We normalize each eigenvector.
Length of $x_1$:
$$
\|x_1\| = \sqrt{1^2 + 2^2} = \sqrt{5}.
$$
Length of $x_2$:
$$
\|x_2\| = \sqrt{(-2)^2 + 1^2} = \sqrt{5}.
$$
Thus orthonormal eigenvectors are
$$
q_1 =
\frac{1}{\sqrt{5}}
\begin{pmatrix}
1 \\
2
\end{pmatrix},
\quad
q_2 =
\frac{1}{\sqrt{5}}
\begin{pmatrix}
-2 \\
1
\end{pmatrix}.
$$
---
#### Step 4: Construct Orthogonal Matrix

We form
$$
Q =
\begin{pmatrix}
\frac{1}{\sqrt{5}} & \frac{-2}{\sqrt{5}} \\
\frac{2}{\sqrt{5}} & \frac{1}{\sqrt{5}}
\end{pmatrix}.
$$
We verify
$$
Q^T Q = I.
$$
---
#### Step 5: Diagonal Matrix

We define
$$
\Lambda =
\begin{pmatrix}
-3 & 0 \\
0 & 2
\end{pmatrix}.
$$
Then
$$
A = Q \Lambda Q^T.
$$
Thus $A$ is orthogonally diagonalized.

---
### 5. Conceptual Understanding

Orthogonal diagonalization provides:
1. A diagonal representation of $A$.
2. Orthonormal eigenvectors.
3. Stability and geometric clarity.

If $A$ is real symmetric, we can always find an orthonormal basis of eigenvectors.

---
### 6. Key Takeaways

- Real symmetric matrices have real eigenvalues.
- Eigenvectors corresponding to distinct eigenvalues are linearly independent.
- Real symmetric matrices are orthogonally diagonalizable.
- Orthogonal diagonalization satisfies
$$
A = Q \Lambda Q^T.
$$
This result is the real case of the spectral theorem.
In subsequent development, this theorem generalizes to Hermitian matrices in complex vector spaces.

---
`**********************************************************************************`

---
## Lecture 5
### Spectral Theorem and Orthogonal Diagonalization

### 1. Spectral Theorem for Real Symmetric Matrices

Let $A$ be a real symmetric $n \times n$ matrix.
The spectral theorem states:
1. All eigenvalues of $A$ are real.
2. Eigenvectors corresponding to distinct eigenvalues are linearly independent.
3. $A$ is orthogonally diagonalizable.

---
### 2. Orthogonal Diagonalization

#### Definition

A matrix $A$ is orthogonally diagonalizable if there exists an orthogonal matrix $Q$ such that
$$
A = Q \Lambda Q^T
$$
where
$$
Q^T Q = I
$$
and
$$
\Lambda =
\begin{pmatrix}
\lambda_1 &        &        \\
          & \ddots &        \\
          &        & \lambda_n
\end{pmatrix}.
$$
Since $Q$ is orthogonal,
$$
Q^{-1} = Q^T.
$$
Thus orthogonal diagonalization is a special case of diagonalization:
$$
A = Q \Lambda Q^{-1},
$$
with the additional constraint
$$
Q^T Q = I.
$$
---
### 3. Important Observations

- Not every real matrix is diagonalizable.
- Every real symmetric matrix is diagonalizable.
- Moreover, it admits an orthogonal diagonalization.

Example of a non diagonalizable matrix:
$$
A =
\begin{pmatrix}
0 & 1 \\
0 & 0
\end{pmatrix}.
$$
---
### 4. Example of Orthogonal Diagonalization

Consider
$$
A =
\begin{pmatrix}
1 & -2 \\
-2 & -2
\end{pmatrix}.
$$
#### Step 1: Eigenvalues

The eigenvalues are
$$
\lambda_1 = -3, \quad \lambda_2 = 2.
$$
#### Step 2: Eigenvectors

Corresponding eigenvectors:
$$
x_1 =
\begin{pmatrix}
1 \\
2
\end{pmatrix},
\quad
x_2 =
\begin{pmatrix}
-2 \\
1
\end{pmatrix}.
$$
---
### 5. Normalization

Compute norms:
$$
\|x_1\| = \sqrt{1^2 + 2^2} = \sqrt{5},
$$
$$
\|x_2\| = \sqrt{(-2)^2 + 1^2} = \sqrt{5}.
$$
Normalized eigenvectors:
$$
q_1 = \frac{1}{\sqrt{5}}
\begin{pmatrix}
1 \\
2
\end{pmatrix},
\quad
q_2 = \frac{1}{\sqrt{5}}
\begin{pmatrix}
-2 \\
1
\end{pmatrix}.
$$
---
### 6. Construct Orthogonal Matrix

Form
$$
Q =
\begin{pmatrix}
\frac{1}{\sqrt{5}} & -\frac{2}{\sqrt{5}} \\
\frac{2}{\sqrt{5}} & \frac{1}{\sqrt{5}}
\end{pmatrix}.
$$
Verify orthogonality:
$$
Q^T Q = I.
$$
---
### 7. Diagonal Matrix
$$
\Lambda =
\begin{pmatrix}
-3 & 0 \\
0 & 2
\end{pmatrix}.
$$
---
### 8. Final Decomposition

Compute
$$
Q \Lambda Q^T.
$$
This yields
$$
A =
\begin{pmatrix}
1 & -2 \\
-2 & -2
\end{pmatrix}.
$$
Thus,
$$
A = Q \Lambda Q^T.
$$
---
### 9. Conceptual Summary

For a real symmetric matrix:
- Eigenvalues are real.
- Eigenvectors corresponding to distinct eigenvalues are orthogonal.
- After normalization, eigenvectors form an orthonormal basis.
- The matrix can be written as
$$
A = Q \Lambda Q^T.
$$
This is orthogonal diagonalization and is a central consequence of the spectral theorem.

---
`**********************************************************************************`

---
