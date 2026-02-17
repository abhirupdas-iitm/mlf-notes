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
## Lecture 1

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
