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
