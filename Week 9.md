## Lecture 1
### Constrained Optimization with One Inequality Constraint

#### Problem Setup

Given functions  
$f : \mathbb{R}^d \to \mathbb{R}$  
$g : \mathbb{R}^d \to \mathbb{R}$  
Consider the optimization problem
$$
\min_x f(x)
$$
subject to
$$
g(x) \le 0
$$
---
### Necessary Conditions for Optimality

Suppose a point $x^*$ is claimed to be optimal.
To verify optimality, we check necessary conditions.
#### 1. Feasibility Condition

The point must satisfy the constraint:
$$
g(x^*) \le 0
$$
If
$$
g(x^*) > 0
$$
then $x^*$ is infeasible and cannot be optimal.

---
#### 2. No Descent Direction Should Be Feasible

If $x^*$ is optimal, then:
There must not exist a direction that
- decreases $f$
- and maintains feasibility

---
### Descent Directions

#### Taylor Expansion

For small step size $\eta$ and direction $d$,
$$
f(x + \eta d) \approx f(x) + \eta d^T \nabla f(x)
$$
A direction $d$ is a descent direction for $f$ at $x$ if
$$
d^T \nabla f(x) < 0
$$
This condition depends only on $f$.
Thus, at $x^*$:
$$
d^T \nabla f(x^*) < 0
$$
characterizes descent directions.
Geometrically, descent directions are all directions making an obtuse angle with $\nabla f(x^*)$.

---
### Feasible Directions

Assume
$$
g(x^*) \le 0
$$
A direction $d$ is feasible if, for sufficiently small $\eta > 0$,
$$
g(x^* + \eta d) \le 0
$$
Using Taylor expansion:
$$
g(x^* + \eta d) \approx g(x^*) + \eta d^T \nabla g(x^*)
$$
If
$$
d^T \nabla g(x^*) < 0
$$
then $g$ decreases further and feasibility is preserved.
Thus, any descent direction of $g$ at $x^*$ is a feasible direction.
This condition depends only on $g$.

---
### Combined Condition

A direction $d$ is
Descent for $f$ if
$$
d^T \nabla f(x^*) < 0
$$
Feasible if
$$
d^T \nabla g(x^*) < 0
$$
If there exists $d$ such that
$$
d^T \nabla f(x^*) < 0
$$
and
$$
d^T \nabla g(x^*) < 0
$$
then
- we can move in direction $d$
- decrease $f$
- remain feasible

Therefore,
$x^*$ cannot be optimal.

---
### Geometric Interpretation

At $x^*$:
- $\nabla f(x^*)$ determines descent half space
- $\nabla g(x^*)$ determines feasible half space

If the descent region of $f$ and the feasible region of $g$ intersect, then
there exists a direction that is both descent and feasible.
In that case, $x^*$ is not optimal.

---
### Key Necessary Condition

If $x^*$ is optimal and satisfies $g(x^*) \le 0$, then
There must not exist any direction $d$ such that
$$
d^T \nabla f(x^*) < 0
$$
and
$$
d^T \nabla g(x^*) < 0
$$
This condition will lead to a structural relationship between
$$
\nabla f(x^*)
$$
and
$$
\nabla g(x^*)
$$
which characterizes constrained optimality.

---
`***********************************************************************************`

---
## Lecture 3

### Relationship Between Gradients at Optimality

Consider the constrained problem
$$
\min_x f(x)
$$
subject to
$$
g(x) \le 0
$$
Let $x^*$ be a feasible point:
$$
g(x^*) \le 0
$$
We seek a necessary condition relating
$$
\nabla f(x^*) \quad \text{and} \quad \nabla g(x^*)
$$
such that no descent direction is feasible.

---
### Case 1: Gradients Point in Same Direction

Assume
$$
\nabla f(x^*) \parallel \nabla g(x^*)
$$
Descent directions satisfy
$$
d^T \nabla f(x^*) < 0
$$
Feasible directions satisfy
$$
d^T \nabla g(x^*) < 0
$$
If the gradients are parallel, then any direction satisfying
$$
d^T \nabla f(x^*) < 0
$$
automatically satisfies
$$
d^T \nabla g(x^*) < 0
$$
Thus every descent direction is feasible.
Therefore, there exists a whole half space of directions that both decrease $f$ and preserve feasibility.
Conclusion:
$x^*$ cannot be optimal.

---
### Case 2: Gradients Anti Parallel

Assume
$$
\nabla f(x^*) \quad \text{and} \quad \nabla g(x^*)
$$
point in opposite directions.
Descent directions satisfy
$$
d^T \nabla f(x^*) < 0
$$
Feasible directions satisfy
$$
d^T \nabla g(x^*) < 0
$$
Since the gradients are anti parallel, the descent half space of $f$ lies on one side, while feasible directions lie on the opposite side.
Thus no direction $d$ can satisfy both
$$
d^T \nabla f(x^*) < 0
$$
and
$$
d^T \nabla g(x^*) < 0
$$
Therefore no descent direction is feasible.

---
### Necessary Condition for Inequality Constraint

The above geometric argument implies:
There exists a scalar $\lambda > 0$ such that
$$
\nabla f(x^*) = - \lambda \nabla g(x^*)
$$
This ensures anti parallel alignment.
This is a necessary condition for optimality for
$$
\min_x f(x) \quad \text{subject to} \quad g(x) \le 0
$$
The scalar $\lambda$ is called the Lagrange multiplier.

---
### Equality Constraint Case

Consider
$$
\min_x f(x)
$$
subject to
$$
g(x) = 0
$$
---
### Feasible Directions

Using Taylor expansion,
$$
g(x^* + \eta d) \approx g(x^*) + \eta d^T \nabla g(x^*)
$$
Since $g(x^*) = 0$, feasibility requires
$$
d^T \nabla g(x^*) = 0
$$
Thus feasible directions lie on the hyperplane perpendicular to $\nabla g(x^*)$.

---
### Descent Directions

Descent directions satisfy
$$
d^T \nabla f(x^*) < 0
$$
---
### Optimal Configuration

For optimality, no direction must satisfy both
$$
d^T \nabla f(x^*) < 0
$$
and
$$
d^T \nabla g(x^*) = 0
$$
This occurs when $\nabla f(x^*)$ is orthogonal to the feasible hyperplane, i.e.,
$$
\nabla f(x^*) \parallel \nabla g(x^*)
$$
or
$$
\nabla f(x^*) \text{ is anti parallel to } \nabla g(x^*)
$$
Thus,
there exists scalar $\lambda$ such that
$$
\nabla f(x^*) = - \lambda \nabla g(x^*)
$$
where $\lambda$ is any real scalar.

---
### Comparison

#### Inequality Constraint
$$
\nabla f(x^*) = - \lambda \nabla g(x^*)
$$
with
$$
\lambda > 0
$$
---
#### Equality Constraint
$$
\nabla f(x^*) = - \lambda \nabla g(x^*)
$$
with
$$
\lambda \in \mathbb{R}
$$
---
### Key Observation

For constrained optimality, the gradient of the objective must lie in the span of the gradient of the constraint.
The scalar $\lambda$ is called the Lagrange multiplier.
This condition provides the foundation for solving constrained optimization problems using the method of Lagrange multipliers.

---
`***********************************************************************************`

---
## Lecture 3
### Method of Lagrange Multipliers

Consider the equality constrained optimization problem
$$
\min_x f(x)
$$
subject to
$$
g(x) = 0
$$
---
### Necessary Conditions for Optimality

If $x^*$ is optimal, then:
#### 1. Feasibility
$$
g(x^*) = 0
$$
#### 2. Gradient Alignment
There exists scalar $\lambda$ such that
$$
\nabla f(x^*) = - \lambda \nabla g(x^*)
$$
For equality constraints,
$$
\lambda \in \mathbb{R}
$$
The scalar $\lambda$ is called the Lagrange multiplier.

---
### Example

Let
$$
f(x_1, x_2) = x_1^2 + 2x_2 + 4x_2^2
$$
Constraint:
$$
g(x_1, x_2) = x_1^2 + x_2^2 - 1
$$
Thus feasible points lie on the unit circle:
$$
x_1^2 + x_2^2 = 1
$$
---
### Step 1: Compute Gradients

Gradient of $f$:
$$
\nabla f(x_1, x_2) =
\begin{pmatrix}
2x_1 \\
2 + 8x_2
\end{pmatrix}
$$
Gradient of $g$:
$$
\nabla g(x_1, x_2) =
\begin{pmatrix}
2x_1 \\
2x_2
\end{pmatrix}
$$
---
### Step 2: Apply Lagrange Condition

We impose
$$
\nabla f = - \lambda \nabla g
$$
This gives the system
$$
\begin{pmatrix}
2x_1 \\
2 + 8x_2
\end{pmatrix}
=
- \lambda
\begin{pmatrix}
2x_1 \\
2x_2
\end{pmatrix}
$$
Which yields componentwise equations:
$$
2x_1 = - \lambda 2x_1
$$
$$
2 + 8x_2 = - \lambda 2x_2
$$
---
### Step 3: Solve System

#### Equation 1
$$
2x_1 + 2\lambda x_1 = 0
$$
$$
2x_1(1 + \lambda) = 0
$$
Thus either
Case A:
$$
\lambda = -1
$$
or
Case B:
$$
x_1 = 0
$$
---
### Case A: $\lambda = -1$

Substitute into Equation 2:
$$
2 + 8x_2 = -(-1)2x_2
$$
$$
2 + 8x_2 = 2x_2
$$
$$
2 + 6x_2 = 0
$$
$$
x_2 = -\frac{1}{3}
$$
Feasibility condition:
$$
x_1^2 + x_2^2 = 1
$$
$$
x_1^2 + \frac{1}{9} = 1
$$
$$
x_1^2 = \frac{8}{9}
$$
$$
x_1 = \pm \frac{\sqrt{8}}{3}
$$
Thus two candidate points:
$$
\left(\frac{\sqrt{8}}{3}, -\frac{1}{3}\right)
$$
$$
\left(-\frac{\sqrt{8}}{3}, -\frac{1}{3}\right)
$$
---
### Case B: $x_1 = 0$

Feasibility:
$$
x_2^2 = 1
$$
$$
x_2 = \pm 1
$$
Thus two candidate points:
$$
(0,1)
$$
$$
(0,-1)
$$
---
### Step 4: Evaluate Objective Function

Recall
$$
f(x_1, x_2) = x_1^2 + 2x_2 + 4x_2^2
$$
#### At $(0,1)$
$$
f = 0 + 2 + 4 = 6
$$
#### At $(0,-1)$
$$
f = 0 - 2 + 4 = 2
$$
#### At $\left(\pm \frac{\sqrt{8}}{3}, -\frac{1}{3}\right)$
$$
x_1^2 = \frac{8}{9}
$$
$$
x_2 = -\frac{1}{3}
$$
$$
x_2^2 = \frac{1}{9}
$$
$$
f = \frac{8}{9} - \frac{2}{3} + \frac{4}{9}
$$
$$
= \frac{12}{9} - \frac{2}{3}
$$
$$
= \frac{4}{3} - \frac{2}{3}
$$
$$
= \frac{2}{3}
$$
---
### Conclusion

Function values:
$$
6, \quad 2, \quad \frac{2}{3}, \quad \frac{2}{3}
$$
Minimum value:
$$
\frac{2}{3}
$$
Minimizers:
$$
\left(\frac{\sqrt{8}}{3}, -\frac{1}{3}\right)
$$
$$
\left(-\frac{\sqrt{8}}{3}, -\frac{1}{3}\right)
$$
Maximum value:
$$
6
$$
at
$$
(0,1)
$$
---
### Projected Gradient Descent

When analytic solution is not feasible, use iterative methods.

---
### Standard Gradient Descent

Initialize:
$$
x_0
$$
Iterate:
$$
x_{t+1} = x_t - \eta \nabla f(x_t)
$$
This may leave the feasible region.

---
### Projection Operator

Let feasible set
$$
S = \{ y : g(y) \le 0 \}
$$
Define projection operator:
$$
\Pi_S(x) = \arg\min_{y \in S} \| x - y \|^2
$$
Projection finds the closest feasible point.

---
### Projected Gradient Descent Algorithm

Initialization:
$$
x_0
$$
For $t = 0,1,\dots,T$:
Gradient step:
$$
z_t = x_t - \eta \nabla f(x_t)
$$
Projection step:
$$
x_{t+1} = \Pi_S(z_t)
$$
---
### Key Observations
1. Every iterate remains feasible.
2. Requires efficient computation of projection.
3. If feasible set is convex, convergence to optimal solution can be guaranteed under suitable conditions.
4. Convex objective functions improve convergence guarantees.
Projected gradient descent extends gradient descent to constrained optimization.

---
`***********************************************************************************`

---
## Lecture 4
### Introduction to Convexity

Optimization algorithms such as gradient descent typically converge to local minima.
To guarantee global optimality, we restrict attention to special classes of functions and sets.
These are based on the notion of convexity.

---
### Convex Sets
#### Definition

Let $S \subseteq \mathbb{R}^d$.
The set $S$ is said to be convex if for all $x_1, x_2 \in S$ and for all $\lambda \in [0,1]$,
$$
\lambda x_1 + (1 - \lambda) x_2 \in S
$$
---
### Interpretation

For any two points in the set, the entire line segment joining them must lie inside the set.
The point
$$
\lambda x_1 + (1 - \lambda) x_2
$$
is called a convex combination of $x_1$ and $x_2$.
Special cases:
If $\lambda = 1$,
$$
\lambda x_1 + (1 - \lambda) x_2 = x_1
$$
If $\lambda = 0$,
$$
\lambda x_1 + (1 - \lambda) x_2 = x_2
$$
If $\lambda = \frac{1}{2}$,
$$
\frac{1}{2} x_1 + \frac{1}{2} x_2
$$
is the midpoint of the segment joining $x_1$ and $x_2$.
As $\lambda$ varies from $0$ to $1$, the point traces the entire line segment.

---
### Examples of Convex Sets

#### 1. Line in $\mathbb{R}^2$

Any line in $\mathbb{R}^2$ is convex.
Given two points on the line, the segment joining them lies entirely on the line.

---
#### 2. Ellipse or Circle

Any filled ellipse or circle is convex.
For any two points inside the ellipse, the entire line segment lies inside the ellipse.

---
#### 3. Non Convex Set

A set with an indentation or gap is not convex.
If there exist $x_1, x_2 \in S$ such that the line segment between them exits the set, then $S$ is not convex.

---
### Convex Sets in One Dimension

If $S \subseteq \mathbb{R}$, then convex sets are exactly intervals of the form
$$
[a,b]
$$
or
$$
(a,b)
$$
or infinite intervals such as
$$
(-\infty, b]
$$
Union of two disjoint intervals is not convex.
If
$$
S = [a,b] \cup [c,d]
$$
with $b < c$, then $S$ is not convex.

---
### Hyperplanes

#### Definition

Given $w \in \mathbb{R}^d$ and scalar $b$, define
$$
S = \{ x \in \mathbb{R}^d : w^T x = b \}
$$
This set is called a hyperplane.

---
### Claim

Hyperplanes are convex sets.

---
#### Proof

Take any $x_1, x_2 \in S$.
Then
$$
w^T x_1 = b
$$
$$
w^T x_2 = b
$$
Consider any $\lambda \in [0,1]$.
Compute:
$$
w^T \big( \lambda x_1 + (1 - \lambda) x_2 \big)
$$
Using linearity:
$$
= \lambda w^T x_1 + (1 - \lambda) w^T x_2
$$
Substitute values:
$$
= \lambda b + (1 - \lambda) b
$$
$$
= b
$$
Therefore,
$$
\lambda x_1 + (1 - \lambda) x_2 \in S
$$
Hence $S$ is convex.

---
### Half Spaces

#### Definition

Given $w \in \mathbb{R}^d$ and scalar $b$, define
$$
S = \{ x \in \mathbb{R}^d : w^T x \le b \}
$$
This set is called a half space.

---
### Convexity of Half Spaces

Take $x_1, x_2 \in S$.
Then
$$
w^T x_1 \le b
$$
$$
w^T x_2 \le b
$$
For $\lambda \in [0,1]$,
$$
w^T \big( \lambda x_1 + (1 - \lambda) x_2 \big)
=
\lambda w^T x_1 + (1 - \lambda) w^T x_2
$$
Since both terms are less than or equal to $b$,
$$
\le \lambda b + (1 - \lambda) b
$$
$$
= b
$$
Therefore,
$$
\lambda x_1 + (1 - \lambda) x_2 \in S
$$
Hence half spaces are convex.

---
### Important Property
#### Intersection of Convex Sets

Let $S_1, S_2 \subseteq \mathbb{R}^d$ be convex.
Define
$$
S = S_1 \cap S_2
$$
Take any $x_1, x_2 \in S$.
Then
$$
x_1, x_2 \in S_1
$$
and
$$
x_1, x_2 \in S_2
$$
Since both sets are convex,
$$
\lambda x_1 + (1 - \lambda) x_2 \in S_1
$$
and
$$
\lambda x_1 + (1 - \lambda) x_2 \in S_2
$$
Thus,
$$
\lambda x_1 + (1 - \lambda) x_2 \in S
$$
Therefore, intersection of convex sets is convex.
Convex sets play a fundamental role in optimization and machine learning, as many feasible regions are intersections of half spaces, and therefore convex.
