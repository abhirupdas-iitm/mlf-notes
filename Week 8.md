## Lecture 1: Introduction to Optimization

### Three Pillars of Machine Learning
Machine learning theory rests on three foundational mathematical pillars:

#### Pillar 1: Linear Algebra
**Role:** Structure and relationships in data.

Linear algebra helps model structural relationships between variables. For example, suppose we collect data on height and weight of individuals:
- Each data point is represented as a vector in $\mathbb{R}^2$.
- A linear relationship between height and weight can be modeled as:

$$
y = wx + b
$$
where:
- $x$ represents height,
- $y$ represents weight,
- $w, b$ are parameters.

This structural modeling relies fundamentally on linear algebra.

---
#### Pillar 2: Probability

**Role:** Modeling noise and uncertainty in data.
In real data:
- Observations do not lie exactly on a single line.
- Deviations occur due to measurement errors, variability, or missing information.
We model these deviations as noise:
$$
y = wx + b + \epsilon
$$
where:
- $\epsilon$ represents uncertainty or noise.

Probability theory provides the mathematical framework to model and reason about such uncertainty.

---
#### Pillar 3: Optimization

**Role:** Converting data into decisions.
There are infinitely many possible lines relating height and weight. The question is:

> Which line best represents the relationship in the observed data?

This requires defining a notion of "best."
Optimization provides the mathematical framework to:
- Compare different models,
- Quantify their performance,
- Select the best one according to a defined criterion.

---
### Example: Height and Weight Prediction

#### Data Representation
Let data be:
$$
\{(x_i, y_i)\}_{i=1}^n
$$
where:
- $x_i$ is height,
- $y_i$ is weight.

We assume a linear model:
$$
\hat{y}_i = wx_i + b
$$
---
#### Multiple Possible Models

There are infinitely many candidate lines:
$$
y = w x + b
$$
Each choice of $w, b$ defines a different line.
Thus, we must choose $(w, b)$ optimally.

---
### Optimization as Decision-Making

#### Objective Function
To determine the best parameters, define a loss function:
$$
L(w,b) = \frac{1}{n} \sum_{i=1}^{n} (y_i - (wx_i + b))^2
$$
The goal is:
$$
\min_{w,b} L(w,b)
$$
This is an optimization problem.

---
### Summary of the Three Pillars

#### Linear Algebra
- Models structure in data.
- Represents data as vectors and matrices.
- Captures linear relationships.

#### Probability

- Models uncertainty and noise.
- Quantifies randomness.
- Allows principled statistical reasoning.

#### Optimization
- Selects the best model among many.
- Converts data and models into decisions.
- Solves problems of the form:
$$
\min_{\theta} f(\theta)
\quad \text{or} \quad
\max_{\theta} f(\theta)
$$
---
### Optimization: Conceptual Definition

**Optimization** is the mathematical discipline concerned with:

> Finding the best element from a set of feasible solutions according to a given objective function.

In machine learning:
- Feasible solutions: model parameters.
- Objective function: loss or risk.
- Best: minimum loss or maximum likelihood.

---
### Core Insight

Machine learning requires:
1. Structure modeling via linear algebra.
2. Uncertainty modeling via probability.
3. Decision selection via optimization.
Together, these three pillars form the foundation upon which machine learning theory is built.

---
`***********************************************************************************`

---
## Lecture 2
### Introduction to Optimization

### The Three Pillars of Machine Learning

Machine learning rests on three foundational mathematical pillars:
1. Linear Algebra  
2. Probability  
3. Optimization  

#### Role of Each Pillar
- Linear Algebra: Models structure and relationships in data.
- Probability: Models uncertainty and noise in data.
- Optimization: Converts data and models into decisions.

Optimization is the mathematical tool that enables selection of the best model, classifier, or representation according to a well-defined criterion.

---
### Why Optimization in Machine Learning

In supervised learning, we seek the best classifier.
Let:
- Input data: labeled examples
- Goal: classify new data points
There are infinitely many possible classifiers. The notion of best must be formalized.

#### Best as Minimization or Maximization
- Best classifier = one with least loss
- Best policy = one with maximum reward

Thus, machine learning problems often reduce to:
$$
\text{minimize loss}
$$
or
$$
\text{maximize reward}
$$
Optimization formalizes these objectives.

---
### Motivating Example: Cow, Rope, Fence, Grass

#### Setup

Field modeled as a 2D plane.
- Cow at position:
$$
(20, 30)
$$
- Rope length:
$$
10
$$
- Fence: vertical line passing through:
$$
(25, 0)
$$
- Grass at:
$$
(40, 40)
$$
---
### Objective: Distance to Grass

Let cow position be:
$$
x = (x_1, x_2)
$$
Distance to grass:
$$
d = \sqrt{(x_1 - 40)^2 + (x_2 - 40)^2}
$$
We minimize squared distance:
$$
(x_1 - 40)^2 + (x_2 - 40)^2
$$
---
### Constraints

#### Rope Constraint

Cow must lie within radius 10 of (20, 30):
$$
(x_1 - 20)^2 + (x_2 - 30)^2 \le 100
$$
#### Fence Constraint

Cow must lie on left side of fence:
$$
x_1 \le 25
$$
---
### Complete Optimization Problem
$$
\min_{x_1, x_2}
(x_1 - 40)^2 + (x_2 - 40)^2
$$
subject to
$$
(x_1 - 20)^2 + (x_2 - 30)^2 \le 100
$$
$$
x_1 \le 25
$$
This is a constrained optimization problem.

---
### General Form of Optimization Problem

Let:
$$
x \in \mathbb{R}^d
$$
#### Objective
$$
\min_{x \in \mathbb{R}^d} f(x)
$$
#### Inequality Constraints
$$
g_i(x) \le 0, \quad i = 1, \dots, k
$$
#### Equality Constraints
$$
h_j(x) = 0, \quad j = 1, \dots, \ell
$$
---
### Terminology

#### Objective Function
Function being minimized or maximized:
$$
f(x)
$$
#### Variable or Parameter
Optimization variable:
$$
x
$$
#### Inequality Constraints
$$
g_i(x) \le 0
$$
#### Equality Constraints
$$
h_j(x) = 0
$$
---
### Standardization of Constraints

Any inequality constraint of form:
$$
a(x) \le b
$$
can be written as:
$$
a(x) - b \le 0
$$
Any equality constraint:
$$
a(x) = b
$$
can be written as:
$$
a(x) - b = 0
$$
Thus the general form is without loss of generality.

---
### Maximization vs Minimization

Maximization:
$$
\max_x f(x)
$$
Equivalent to:
$$
\min_x -f(x)
$$
Thus all optimization problems can be written in minimization form.

---
### Key Observations
1. Optimization converts structure and uncertainty into decisions.
2. Every machine learning algorithm ultimately solves an optimization problem.
3. Optimization problems consist of:
   - Objective
   - Variables
   - Constraints
4. Both minimization and maximization reduce to minimization.
Next step: developing algorithms to solve optimization problems.

---
`***********************************************************************************`

---
## Lecture 3
### Solving an Unconstrained Optimization Problem Part 1

### Unconstrained Optimization

General unconstrained problem:
$$
\min_{x \in \mathbb{R}} f(x)
$$
No inequality or equality constraints.

---
### Simple Example
$$
\min_{x \in \mathbb{R}} (x - 5)^2
$$
#### Direct Reasoning
- Function is nonnegative.
- Value is zero at $x = 5$.

Thus:
$$
x^\star = 5
$$
$$
f(x^\star) = 0
$$
---
### Derivative Based Approach

Let:
$$
f(x) = (x - 5)^2
$$
Compute derivative:
$$
f'(x) = 2(x - 5)
$$
Set derivative to zero:
$$
f'(x) = 0
$$
$$
2(x - 5) = 0
$$
$$
x = 5
$$
This works for simple problems, but does not scale well.

---
### Harder Example
$$
\min_{x \in \mathbb{R}} 3x^6 + 2x^5 + 3x^3 + 5x^2 + 2
$$
Derivative:
$$
f'(x) = 18x^5 + 10x^4 + 9x^2 + 10x
$$
Setting:
$$
f'(x) = 0
$$
Leads to solving a degree 5 polynomial, which is not straightforward.
Thus, need a systematic, iterative algorithm.

---
### Iterative Optimization Framework

Start with:
$$
x_0 \in \mathbb{R}
$$
Iterative update:
$$
x_{t+1} = x_t + d
$$
where $d$ is a direction to move.
Goal: choose $d$ so that the objective decreases.

---
### Understanding Direction for the Example

Recall:
$$
f(x) = (x - 5)^2
$$
Derivative:
$$
f'(x) = 2(x - 5)
$$
#### Observations
- If $x > 5$, then $f'(x) > 0$
- If $x < 5$, then $f'(x) < 0$

Desired movement:
- If $x > 5$, move left
- If $x < 5$, move right

Thus:
- If $x > 5$, want $d < 0$
- If $x < 5$, want $d > 0$

---
### Choosing Direction

Since:
- $f'(x) > 0$ when $x > 5$
- $f'(x) < 0$ when $x < 5$

Opposite sign gives desired direction.
Choose:
$$
d = - f'(x)
$$
Thus update rule becomes:
$$
x_{t+1} = x_t - f'(x_t)
$$
For this example:
$$
x_{t+1} = x_t - 2(x_t - 5)
$$
---
### Example Iterations

Let:
$$
x_0 = 10
$$
#### Step 1
Compute direction:
$$
d_0 = - f'(x_0) = - 2(10 - 5) = -10
$$
Update:
$$
x_1 = 10 - 10 = 0
$$
---
#### Step 2
Compute direction at $x_1 = 0$:
$$
d_1 = - f'(0) = - 2(0 - 5) = 10
$$
Update:
$$
x_2 = 0 + 10 = 10
$$
---
#### Step 3
$$
x_3 = 0
$$
Thus sequence oscillates:
$$
10 \rightarrow 0 \rightarrow 10 \rightarrow 0 \rightarrow \dots
$$
---
### Key Observation

The direction is correct, but the step size is too large.
Problem is not:
- Direction of movement

Problem is:
- Magnitude of movement

We overshoot the minimum at $x = 5$.
Findings from this example:
1. Direction should depend on $x$
2. Negative derivative gives correct direction
3. Step size must be controlled

This motivates introducing a scaling factor in the update rule.

---
`***********************************************************************************`

---
## Lecture 4
### Solving an Unconstrained Optimization Problem Part 2

### Recap: Gradient Based Update
We consider an unconstrained optimization problem:
$$
\min_{x \in \mathbb{R}} f(x)
$$
The iterative update rule is:
$$
x_{t+1} = x_t - \eta_t f'(x_t)
$$
Where:
- $f'(x_t)$ determines the direction
- $\eta_t > 0$ is a scalar step size
- $-\!f'(x_t)$ is the descent direction

The issue observed earlier:
- Direction is correct.
- Step magnitude may be too large.
- This can cause oscillations.

Hence we introduce a step size.

---
### Step Size

Updated rule:
$$
x_{t+1} = x_t - \eta_t f'(x_t)
$$
Where:
- $\eta_t$ is positive
- It may depend on iteration $t$
- It controls how far we move in the descent direction
---
### First Attempt at Step Size

Consider:
$$
\eta_0 = 1, \quad \eta_1 = \frac{1}{2}, \quad \eta_2 = \frac{1}{4}, \quad \eta_3 = \frac{1}{8}, \dots
$$
General form:
$$
\eta_t = \frac{1}{2^t}
$$
Properties:
- Step size decreases geometrically.
- Appears reasonable to avoid oscillation.
#### Cumulative Step Size
Consider total movement if direction is constant:
$$
\sum_{t=0}^{\infty} \eta_t = \sum_{t=0}^{\infty} \frac{1}{2^t}
$$
This is a geometric series:
$$
1 + \frac{1}{2} + \frac{1}{4} + \frac{1}{8} + \dots = 2
$$
Thus:
$$
\sum_{t=0}^{\infty} \eta_t = 2
$$
#### Observation
- Total movement is bounded.
- Even after infinitely many steps, we can move at most 2 units.
- If optimum is farther away, we will never reach it.
- Hence this step size sequence is not suitable.

---
### Desired Properties of Step Sizes

We need:
1. Step size decreases to avoid oscillations.
2. Cumulative step sizes should not be bounded.

That is:
$$
\eta_t \to 0
$$
and
$$
\sum_{t=0}^{\infty} \eta_t = \infty
$$
---
### Improved Step Size Sequence

Consider:
$$
\eta_0 = 1, \quad \eta_1 = \frac{1}{2}, \quad \eta_2 = \frac{1}{3}, \quad \eta_3 = \frac{1}{4}, \dots
$$
General form:
$$
\eta_t = \frac{1}{t+1}
$$
#### Cumulative Sum
$$
\sum_{t=0}^{\infty} \eta_t
=
\sum_{t=0}^{\infty} \frac{1}{t+1}
=
1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \dots
$$
This is the harmonic series.
Key property:
$$
\sum_{t=0}^{\infty} \frac{1}{t+1} = \infty
$$
---
### Important Observations
- Step size decreases to zero.
- Total cumulative movement is unbounded.
- No matter how far the starting point is from optimum, it is theoretically possible to reach the optimum.
- Avoids oscillation from large constant step sizes.
- Avoids stagnation from overly fast geometric decay.

---
### Final Iterative Algorithm

Given objective:
$$
\min_{x \in \mathbb{R}} f(x)
$$
Algorithm:
1. Initialize $x_0$.
2. For $t = 0,1,2,\dots,T$:
$$
x_{t+1} = x_t - \eta_t f'(x_t)
$$
with
$$
\eta_t = \frac{1}{t+1}
$$
3. Output $x_T$.
---
### Conceptual Insight

Two conflicting objectives:
- Reduce step size to avoid oscillations.
- Maintain sufficient total movement to reach optimum.

The harmonic step size balances both:
- $\eta_t \to 0$
- $\sum \eta_t = \infty$

This completes the construction of a principled step size schedule for gradient based optimization.

---
`***********************************************************************************`

---
