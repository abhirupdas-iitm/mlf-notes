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
