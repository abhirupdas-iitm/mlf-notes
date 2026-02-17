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
