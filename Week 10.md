## Lecture 1
### Convex Functions: Optimality and Additional Properties

### Reminder: Local vs Global Minima
If $f$ is convex, then
all local minima are global minima.
This does not imply uniqueness of the global minimum.

---
### Non-Uniqueness of Global Minima

For $f : \mathbb{R} \to \mathbb{R}$ convex,
the set of all global minima can be an interval.
Fact:
The set of all global minima of a convex function is a convex set.
For $f : \mathbb{R} \to \mathbb{R}$, this set must be an interval.

---
### Necessary and Sufficient Condition for Optimality
We now study optimality conditions for differentiable convex functions.
#### Problem
Minimize
$$
f(x)
$$
where $f : \mathbb{R}^d \to \mathbb{R}$ is convex and differentiable.

---
### Theorem

Let $f : \mathbb{R}^d \to \mathbb{R}$ be differentiable and convex.
Then
$$
x^* \text{ is a global minimum}
\quad
\iff
\quad
\nabla f(x^*) = 0
$$
---
### Proof Sketch

#### Necessity
Assume $x^*$ is a global minimum.
Then $x^*$ is also a local minimum.
Suppose
$$
\nabla f(x^*) \ne 0
$$
Then consider moving in direction
$$
d = - \nabla f(x^*)
$$
Using first-order Taylor approximation,
for sufficiently small $\eta > 0$,
$$
f(x^* + \eta d)
<
f(x^*)
$$
This contradicts global minimality.
Hence
$$
\nabla f(x^*) = 0
$$
Note: convexity is not required for this direction.

---
### Sufficiency

Assume
$$
\nabla f(x^*) = 0
$$
Use first-order convexity condition:
For all $x, y \in \mathbb{R}^d$,
$$
f(y)
\ge
f(x) + \nabla f(x)^T (y - x)
$$
Set $x = x^*$:
$$
f(y)
\ge
f(x^*) + \nabla f(x^*)^T (y - x^*)
$$
Since
$$
\nabla f(x^*) = 0
$$
we obtain
$$
f(y)
\ge
f(x^*)
\quad
\forall y
$$
Thus $x^*$ is a global minimum.
Convexity is essential for this direction.

---
### Conclusion

For differentiable convex functions:
$$
\nabla f(x^*) = 0
$$
is both necessary and sufficient for global optimality.

---
### Implication for Gradient Descent

Gradient descent converges to a point where
$$
\nabla f(x) = 0
$$
For convex functions, this guarantees global optimality.

---
### Additional Properties of Convex Functions
#### Property 1: Sum of Convex Functions
Let
$$
f, g : \mathbb{R}^d \to \mathbb{R}
$$
be convex.
Define
$$
h(x) = f(x) + g(x)
$$
Then $h$ is convex.
#### Proof
For any $x, y$ and $\lambda \in [0,1]$:
$$
h(\lambda x + (1-\lambda)y)
=
f(\lambda x + (1-\lambda)y)
+
g(\lambda x + (1-\lambda)y)
$$
Using convexity of $f$ and $g$:
$$
\le
\lambda f(x) + (1-\lambda)f(y)
+
\lambda g(x) + (1-\lambda)g(y)
$$
$$
=
\lambda h(x) + (1-\lambda)h(y)
$$
Hence $h$ is convex.

---
### Property 2: Composition with Non-Decreasing Convex Function

Let
$$
f : \mathbb{R} \to \mathbb{R}
$$
be convex and non-decreasing.
Let
$$
g : \mathbb{R}^d \to \mathbb{R}
$$
be convex.
Define
$$
h(x) = f(g(x))
$$
Then $h$ is convex.
#### Proof Idea

For $\lambda \in [0,1]$:
$$
h(\lambda x + (1-\lambda)y)
=
f(g(\lambda x + (1-\lambda)y))
$$
By convexity of $g$:
$$
g(\lambda x + (1-\lambda)y)
\le
\lambda g(x) + (1-\lambda)g(y)
$$
Since $f$ is non-decreasing:
$$
f(g(\lambda x + (1-\lambda)y))
\le
f(\lambda g(x) + (1-\lambda)g(y))
$$
By convexity of $f$:
$$
\le
\lambda f(g(x)) + (1-\lambda)f(g(y))
$$
Thus $h$ is convex.

---
### Property 3: Composition with Linear Function

Let
$$
f : \mathbb{R} \to \mathbb{R}
$$
be convex.
Let
$$
g : \mathbb{R}^d \to \mathbb{R}
$$
be linear.
Define
$$
h(x) = f(g(x))
$$
Then $h$ is convex.
#### Proof

Linearity implies
$$
g(\lambda x + (1-\lambda)y)
=
\lambda g(x) + (1-\lambda)g(y)
$$
Then convexity of $f$ gives
$$
h(\lambda x + (1-\lambda)y)
\le
\lambda h(x) + (1-\lambda)h(y)
$$
---
### Important Remark

In general,
if both $f$ and $g$ are convex,
the composition $f \circ g$ need not be convex.
#### Counterexample

Let
$$
g(x) = x^2
$$
which is convex.
Let
$$
f(x) = e^{-x}
$$
Since $e^x$ is convex and $-x$ is linear,
$f(x) = e^{-x}$ is convex.
But
$$
f(g(x)) = e^{-x^2}
$$
This function is not convex.
Thus composition of convex functions is not convex in general.

---
### Concave Functions

A function $g$ is concave if
$$
- g
$$
is convex.
Example:
$$
g(x) = -x^2
$$
is concave.
These structural properties allow us to build complex convex functions from simpler ones, which is essential in machine learning optimization.

---
`***********************************************************************************`

---
## Lecture 2
### Applications of Optimization to Machine Learning
### Linear Regression

#### Dataset
Training data consists of
$$
\{(x_i, y_i)\}_{i=1}^n
$$
where
- $x_i \in \mathbb{R}^d$
- $y_i \in \mathbb{R}$
Goal: Learn a function
$$
h : \mathbb{R}^d \to \mathbb{R}
$$
such that for a new test point $x_{\text{test}}$,
$$
\hat y_{\text{test}} = h(x_{\text{test}})
$$
---
### Linear Hypothesis Class

In linear regression, we restrict $h$ to be linear:
$$
h(x) = w^\top x
$$
where $w \in \mathbb{R}^d$.
Thus learning $h$ reduces to learning $w$.

---
### Performance Measure

Define the sum of squared errors:
$$
f(w) = \sum_{i=1}^n (w^\top x_i - y_i)^2
$$
Often scaled as
$$
f(w) = \frac{1}{2} \sum_{i=1}^n (w^\top x_i - y_i)^2
$$
Optimization problem:
$$
\min_{w \in \mathbb{R}^d} f(w)
=
\min_{w \in \mathbb{R}^d}
\frac{1}{2}
\sum_{i=1}^n (w^\top x_i - y_i)^2
$$
---
### Convexity of the Objective

Write
$$
f(w) = \sum_{i=1}^n h_i(w)
$$
where
$$
h_i(w) = (w^\top x_i - y_i)^2
$$
Each $h_i(w)$ is a composition:
- $g(w) = w^\top x_i - y_i$ which is linear in $w$
- $\phi(z) = z^2$ which is convex
Since composition of convex function with linear function is convex,
$$
h_i(w) \text{ is convex}
$$
Since sum of convex functions is convex,
$$
f(w) \text{ is convex}
$$
---
### Matrix Formulation

Define
- $X \in \mathbb{R}^{n \times d}$ with rows $x_i^\top$
- $w \in \mathbb{R}^d$
- $y \in \mathbb{R}^n$

Then
$$
f(w) =
\frac{1}{2} \|Xw - y\|_2^2
$$
Equivalent quadratic form:
$$
f(w)
=
\frac{1}{2}
(Xw - y)^\top (Xw - y)
$$
Expand:
$$
f(w)
=
\frac{1}{2}
\left(
w^\top X^\top X w
-
2 w^\top X^\top y
+
y^\top y
\right)
$$
---
### Gradient Computation

Compute gradient:
$$
\nabla f(w)
=
X^\top X w - X^\top y
$$
---
### Optimality Condition

Since $f$ is convex and differentiable,
global minimum satisfies
$$
\nabla f(w^*) = 0
$$
Thus
$$
X^\top X w^* = X^\top y
$$
If $X^\top X$ is invertible:
$$
w^* = (X^\top X)^{-1} X^\top y
$$
If not invertible:
$$
w^* = (X^\top X)^\dagger X^\top y
$$
where $\dagger$ denotes pseudo inverse.
This is the analytical solution.

---
### Computational Considerations

Matrix inversion cost:
$$
O(d^3)
$$
When $d$ is large, this becomes computationally expensive.

---
### Gradient Descent Alternative

Iterative update:
$$
w_{t+1}
=
w_t
-
\eta_t \nabla f(w_t)
$$
Using
$$
\nabla f(w_t)
=
X^\top X w_t - X^\top y
$$
No matrix inversion required.
Convexity guarantees convergence to global optimum.

---
### Stochastic Gradient Descent

Full gradient requires entire dataset.
When $n$ is large:
- Sample small subset of data uniformly at random.
- Compute approximate gradient.
- Update:
$$
w_{t+1}
=
w_t
-
\eta_t \tilde \nabla f(w_t)
$$
where $\tilde \nabla f$ is gradient using sampled data.
Under suitable conditions,
$$
\frac{1}{T}
\sum_{t=1}^T w_t
\to
w^*
$$
as $T \to \infty$.

---
### Key Takeaways

1. Sum of squared errors is convex.
2. Convexity guarantees global optimality via first order condition.
3. Closed form solution exists.
4. For large scale problems, gradient descent avoids expensive matrix inversion.
5. Stochastic gradient descent scales to massive datasets.
Convex optimization provides both theoretical guarantees and practical algorithms for machine learning.

---
`***********************************************************************************`

---
