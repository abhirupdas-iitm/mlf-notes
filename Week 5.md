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
