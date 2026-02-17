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
