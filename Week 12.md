## Lecture 1

## Standard Normal Vector

Let
$$
z_1, z_2, \dots, z_d \sim \mathcal{N}(0,1)
$$
be independent standard normal random variables.

Define the random vector
$$
z = \begin{bmatrix}
z_1 \\
\vdots \\
z_d
\end{bmatrix}.
$$

Since the components are independent, the joint density is
$$
f_Z(z) = \prod_{i=1}^{d} \frac{1}{\sqrt{2\pi}} \exp\left(-\frac{1}{2} z_i^2\right).
$$

Using
$$
\sum_{i=1}^d z_i^2 = \|z\|^2,
$$
we obtain the compact form
$$
f_Z(z) = \frac{1}{(2\pi)^{d/2}} \exp\left(-\frac{1}{2} \|z\|^2\right).
$$

---

## Simple Linear Transform of a 2D Standard Normal

Let
$$
z = \begin{bmatrix} z_1 \\ z_2 \end{bmatrix}, 
\quad z_1, z_2 \sim \mathcal{N}(0,1), \text{ independent}.
$$

Define
$$
x_1 = z_1,
$$
$$
x_2 = \rho z_1 + \sqrt{1-\rho^2} \, z_2,
$$
where $-1 < \rho < 1$.

In matrix form,
$$
x = Az,
$$
with
$$
A =
\begin{bmatrix}
1 & 0 \\
\rho & \sqrt{1-\rho^2}
\end{bmatrix}.
$$

The inverse is
$$
A^{-1} =
\begin{bmatrix}
1 & 0 \\
-\frac{\rho}{\sqrt{1-\rho^2}} & \frac{1}{\sqrt{1-\rho^2}}
\end{bmatrix}.
$$

Determinants:
$$
\det(A) = \sqrt{1-\rho^2},
$$
$$
\det(A^{-1}) = \frac{1}{\sqrt{1-\rho^2}}.
$$

---

## Mean and Covariance

Mean:
$$
\mathbb{E}[x_1] = 0, \quad \mathbb{E}[x_2] = 0.
$$

Variance:
$$
\mathrm{Var}(x_1) = 1,
$$
$$
\mathrm{Var}(x_2) = \rho^2 + (1-\rho^2) = 1.
$$

Covariance:
$$
\mathrm{Cov}(x_1,x_2) = \mathbb{E}[x_1 x_2] = \rho.
$$

Covariance matrix:
$$
\Sigma =
\begin{bmatrix}
1 & \rho \\
\rho & 1
\end{bmatrix}.
$$

Observe:
$$
\Sigma = AA^\top.
$$

Determinant:
$$
\det(\Sigma) = 1-\rho^2.
$$

Inverse:
$$
\Sigma^{-1} = \frac{1}{1-\rho^2}
\begin{bmatrix}
1 & -\rho \\
-\rho & 1
\end{bmatrix}.
$$

---

## Density via Change of Variables

Using change of variables,
$$
f_X(x) = f_Z(A^{-1}x) |\det(A^{-1})|.
$$

Since
$$
f_Z(z) = \frac{1}{2\pi} \exp\left(-\frac{1}{2}\|z\|^2\right),
$$
we obtain
$$
f_X(x) =
\frac{1}{2\pi \sqrt{1-\rho^2}}
\exp\left(-\frac{1}{2} x^\top \Sigma^{-1} x\right).
$$

Explicitly,
$$
f_X(x_1,x_2) =
\frac{1}{2\pi \sqrt{1-\rho^2}}
\exp\left(
-\frac{1}{2(1-\rho^2)}
\left(x_1^2 - 2\rho x_1 x_2 + x_2^2\right)
\right).
$$

---

## Factorization and Conditional Distributions

The joint density factorizes as
$$
f_{X_1,X_2}(x_1,x_2)
=
f_{X_1}(x_1)
f_{X_2|X_1}(x_2|x_1).
$$

Marginal:
$$
X_1 \sim \mathcal{N}(0,1).
$$

Conditional:
$$
X_2 \mid X_1=x_1
\sim
\mathcal{N}(\rho x_1,\, 1-\rho^2).
$$

By symmetry,
$$
X_2 \sim \mathcal{N}(0,1),
$$
$$
X_1 \mid X_2=x_2
\sim
\mathcal{N}(\rho x_2,\, 1-\rho^2).
$$

---

## General Bivariate Normal

Let
$$
x = Az + \mu,
$$
where
$$
z \sim \mathcal{N}(0,I),
$$
and
$$
\Sigma = AA^\top.
$$

Then
$$
x \sim \mathcal{N}(\mu,\Sigma),
$$
with density
$$
f_X(x) =
\frac{1}{2\pi \sqrt{\det(\Sigma)}}
\exp\left(
-\frac{1}{2}(x-\mu)^\top
\Sigma^{-1}
(x-\mu)
\right).
$$

General covariance form:
$$
\Sigma =
\begin{bmatrix}
a^2 & \rho ab \\
\rho ab & b^2
\end{bmatrix},
$$
with $a>0$, $b>0$, $|\rho|<1$.

---

## Multivariate Normal in Dimension $d$

Let
$$
x = Az + \mu,
$$
where
$$
z \sim \mathcal{N}(0,I_d),
$$
and
$$
\Sigma = AA^\top.
$$

Then
$$
x \sim \mathcal{N}(\mu,\Sigma),
$$
with density
$$
f_X(x)
=
\frac{1}{(2\pi)^{d/2}\sqrt{\det(\Sigma)}}
\exp\left(
-\frac{1}{2}
(x-\mu)^\top
\Sigma^{-1}
(x-\mu)
\right).
$$

Mean:
$$
\mathbb{E}[x] = \mu.
$$

Covariance:
$$
\mathrm{Cov}(x) = \Sigma.
$$

---

## Important Properties

Let
$$
x \sim \mathcal{N}(\mu,\Sigma).
$$

### Linear Scalar Transform

If
$$
y = a^\top x,
$$
then
$$
y \sim \mathcal{N}(a^\top \mu,\; a^\top \Sigma a).
$$

### Linear Vector Transform

If
$$
y = Bx,
$$
then
$$
y \sim \mathcal{N}(B\mu,\; B\Sigma B^\top).
$$

### Independence Property

For components $x_i$ and $x_j$ of a multivariate normal:
$$
x_i \text{ and } x_j \text{ independent}
\iff
\Sigma_{ij} = 0.
$$

Uncorrelated components of a multivariate normal are independent.

---
`***********************************************************************************`

---
