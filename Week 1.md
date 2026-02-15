## Lecture 1
### Introduction, Terminology and Setup

---
## 1. What is Machine Learning?

### Definition
Machine Learning (ML) is the study of computer algorithms that improve automatically through experience and by the use of data.

Formally, ML can be viewed as learning a function:
$$
f : \mathcal{X} \rightarrow \mathcal{Y}
$$
Where:

- $\mathcal{X}$ = input space  
- $\mathcal{Y}$ = output space  
- $f$ = unknown mapping rule  

The goal of ML is to approximate $f$ using data.

---
## 2. What is a Task?

A **Task** is a process that converts input into output.
$$
\text{Task}: x \rightarrow y
$$
Where:

- $x \in \mathcal{X}$
- $y \in \mathcal{Y}$

### Examples

- Weather prediction: Radar Map $\rightarrow$ Rain / No Rain  
- Face detection: Image $\rightarrow$ Face / No Face  
- Password verification: Password $\rightarrow$ Authentication  

---
## 3. Task Hierarchy

There are four abstraction levels.
### Level 1: Manual Labour
Input $\rightarrow$ Human $\rightarrow$ Output  
Human directly computes:
$$
y = f(x)
$$
---

### Level 2 & 3: Tool Usage / Programming

Human explicitly writes:
$$
y = f(x)
$$
Structure:
Input $\rightarrow$ Software $\rightarrow$ Output  
Here, the human knows $f$.

---
### Level 4: Machine Learning

Human does not explicitly write $f$.

Instead, we provide labeled data:

$$
\{(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\}
$$

The system learns an approximation:
$$
\hat{f}(x) \approx f(x)
$$

Structure:
Data + Model Design $\rightarrow \hat{f}$  
Then:
$x \rightarrow \hat{f}(x) \rightarrow y$

**Key Idea:** The function is learned from data.

---

## 4. When Should We Use Machine Learning?

### Programming / Human Labour Fails When

- Scale, speed, or cost is too high  
- Cannot express rules mathematically  
- Exact rule $f$ is unknown  

Formally, we cannot define:

$$
y = f(x)
$$

---
### Machine Learning Can Succeed If

- There exists some function $f$  
- We have sufficient data  
- There is underlying structure  

We assume:
$$
\exists f \text{ such that } y = f(x)
$$
We approximate:
$$
\hat{f} = \arg\min_{g \in \mathcal{H}} \mathcal{L}(g(x), y)
$$
Where:

- $\mathcal{H}$ = hypothesis space  
- $\mathcal{L}$ = loss function  
---
## 5. Case Study: Password Verification

Task:
Password $\rightarrow$ Authentication  
Rule:
$$
f(x) =
\begin{cases}
1 & \text{if } x = x_{\text{stored}} \\
0 & \text{otherwise}
\end{cases}
$$
Conclusion:

- Programming works  
- ML not required  
---
## 6. Case Study: Face Detection

Task:
$$
\text{Image} \rightarrow \{0,1\}
$$
Where:

- $1$ = Face  
- $0$ = Not Face  

We cannot explicitly write:
$$
f(\text{pixels}) = \text{Face}
$$
Instead, we collect labeled data:
$$
\{(x_i, y_i)\}_{i=1}^{n}
$$
And learn:
$$
\hat{f}(x)
$$
Classification setting:
$$
y \in \{0,1\}
$$
This is a binary classification problem.

---
## 7. Case Study: Weather Prediction

Task:

Radar Map $\rightarrow$ Rain / Shine  
There exists some unknown function:
$$
y = f(x)
$$
But:

- Humans do not know $f$  
- Cannot code $f$  
- Cannot compute $f$ manually  

We assume:
$$
\exists f
$$
And approximate:

$$
\hat{f}(x) \approx f(x)
$$
---
## 8. Real-World ML Applications

### Spam Classification

Email $\rightarrow \{\text{Spam}, \text{Not Spam}\}$  
Learn:
$$
\hat{f}(\text{email features})
$$
---
### Recommender Systems

User History $\rightarrow$ Recommended Item  
Predict:
$$
\hat{y} = \hat{f}(x)
$$
---
### Smart Assistants

Audio waveform $\rightarrow$ Text  
Text $\rightarrow$ Command  
Both are learned mappings.

---
### Robotics

Environment State $\rightarrow$ Action  
Learn policy:
$$
\pi(s) = a
$$
Where:

- $s$ = state  
- $a$ = action  
---
## 9. Core Mathematical Insight

Machine Learning assumes:

- There exists a function $f$  
- We cannot explicitly write $f$  
- Data contains information about $f$  

So we:

1. Define hypothesis space $\mathcal{H}$  
2. Choose loss function $\mathcal{L}$  

Learn:
$$
\hat{f} = \arg\min_{g \in \mathcal{H}} \mathcal{L}(g(x), y)
$$
This is the fundamental ML framework.

---
`***********************************************************************************`

---
## Lecture 2
### Data, Models and ML Tasks

---
## 1. What is Data?

Data in machine learning is typically a collection of vectors.
Formally, a dataset can be written as:
$$
\mathcal{D} = \{x_1, x_2, \dots, x_n\}
$$
Where:

- $x_i \in \mathbb{R}^d$
- $d$ = number of features (dimension)

Each data point is a vector:
$$
x_i = (x_{i1}, x_{i2}, \dots, x_{id})
$$
---
### Example: Housing Data

Suppose each house is represented as:
$$
x = (\text{\#rooms}, \text{area}, \text{distance to metro}, \text{price})
$$
Example dataset:
$$
x_1 = (3, 9, 1.9, 5.0)
$$
$$
x_2 = (2, 7, 2.1, 3.2)
$$
$$
x_3 = (4, 12, 2.8, 6.6)
$$
and so on.

---
### Metadata

Metadata = information about the data.
Example metadata:
- Feature 1: Number of rooms  
- Feature 2: Area (in 100 sq. ft.)  
- Feature 3: Distance to metro (km)  
- Feature 4: Price (in 10 lakhs)  

Important:
- Computers only need consistency.
- Humans need metadata for interpretability.

---
## 2. What is a Model?

A model is a mathematical simplification of reality.
Formally:
A model is a function:
$$
f : \mathcal{X} \rightarrow \mathcal{Y}
$$
that approximates real-world behavior.

---
### Scientific Examples of Models

- Ideal Gas Law:
$$
PV = nRT
$$
- Newton’s Gravitational Law:
$$
F = \frac{G m_1 m_2}{r^2}
$$
- Moore’s Law (trend model)
- Economic models (e.g., Cobb–Douglas)

Key philosophical insight:

> "All models are wrong, but some are useful."  
> — George Box

Models are approximations, not reality.

---
## 3. Types of Models in Machine Learning

Two major types:

- Predictive Models
- Probabilistic Models
---
## 4. Predictive Models

Predictive models map input to output:
$$
x \rightarrow y
$$
They are used for prediction on unseen data.

Two major types:
- Regression
- Classification
---
### 4.1 Regression Model

Used when output is real-valued.
$$
y \in \mathbb{R}
$$
Example: Predict house price.

Model form:
$$
\text{Price} = a \cdot \text{Area} - \text{Distance}
$$
More generally:
$$
y = a \cdot x_1 + b \cdot x_2 + c \cdot x_3
$$
Where:

- $a, b, c$ = parameters
- $x_1, x_2, x_3$ = features

Regression predicts continuous values.

---
### 4.2 Classification Model

Used when output is discrete.
$$
y \in \{0,1\}
$$
or more generally:
$$
y \in \{1,2,\dots,K\}
$$
Example:

Predict whether house is within 2 km of metro.
Possible outputs:
- Close
- Far
Example model:
$$
\text{Answer} =
\begin{cases}
\text{Close} & \text{if } 2 \cdot \text{Rooms} - \text{Price} < 1 \\
\text{Far} & \text{otherwise}
\end{cases}
$$
Classification predicts categories.

---
## 5. Probabilistic Models

Probabilistic models evaluate likelihood.
They do not directly predict a value.
They compute:
$$
P(x)
$$
or
$$
P(y \mid x)
$$
Examples:

- What is the probability a randomly chosen person is at latitude-longitude $(25^\circ N, 30^\circ E)$?
- What is the probability a tweet was generated by a specific person?

Probabilistic models score configurations of reality.

---
## 6. Learning Algorithms

Learning Algorithms convert:
$$
\text{Data} \rightarrow \text{Model}
$$
They choose from a family of models with same structure but different parameters.

Example model structure:
$$
\text{Price} = a \cdot (\text{Area}) + b \cdot (\text{\#Rooms}) + c \cdot (\text{Distance})
$$
Parameters:
$$
a, b, c
$$
The learning algorithm chooses the best parameters using data.

Formally:
$$
\theta^* = \arg\min_{\theta} \mathcal{L}(f_\theta(x), y)
$$
Where:

- $\theta$ = model parameters
- $\mathcal{L}$ = loss function
---
## 7. Machine Learning Pipeline (Revisited)

Human does not directly write the final model.
Instead:
1. Human specifies model structure.
2. Learning algorithm uses data.
3. Parameters are learned.
4. Final model is produced.

Pipeline:
$$
\text{Human} + \text{Data} \rightarrow \text{Learning Algorithm} \rightarrow \text{Model}
$$
Then:
$$
\text{Input} \rightarrow \text{Model} \rightarrow \text{Output}
$$
---
## Core Idea of This Lecture

- Data = collection of vectors
- Model = mathematical simplification
- Predictive models = regression & classification
- Probabilistic models = likelihood evaluation
- Learning algorithm = data to model converter

---
`***********************************************************************************`

---
## Lecture 3
### Supervised Learning – Regression

---
## 1. Supervised Learning

Supervised learning can be viewed as **curve fitting**.
Given training data:
$$
\{(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\}
$$
Where:
- $x_i \in \mathbb{R}^d$
- $y_i \in \mathcal{Y}$

Goal:
Find a model
$$
f : \mathbb{R}^d \rightarrow \mathcal{Y}
$$
such that:
$$
f(x_i) \text{ is close to } y_i
$$
---
## 2. Notation

- $\mathbb{R}$ = real numbers  
- $\mathbb{R}_+$ = positive reals  
- $\mathbb{R}^d$ = $d$-dimensional real vectors  

Vector notation:

- $x = (x_1, x_2, \dots, x_d)$  
- $x_j$ = $j^{th}$ coordinate  
- $\|x\|$ = Euclidean norm  

$$
\|x\|^2 = \sum_{j=1}^d x_j^2
$$
$$
\|x\| = \sqrt{\sum_{j=1}^d x_j^2}
$$

Collection of vectors:
$$
x^1, x^2, \dots, x^n
$$
- $x^i_j$ = $j^{th}$ coordinate of $i^{th}$ vector  

Indicator function:
$$
\mathbf{1}(\text{predicate}) =
\begin{cases}
1 & \text{if true} \\
0 & \text{if false}
\end{cases}
$$
Example:
$$
\mathbf{1}(2 \text{ is even}) = 1
$$
$$
\mathbf{1}(2 \text{ is odd}) = 0
$$
---
## 3. Regression

Regression is used when:
$$
y_i \in \mathbb{R}
$$
Example:
Predict house price from:
- Rooms
- Area
- Distance to metro

Training data:
$$
\{(x^1, y^1), (x^2, y^2), \dots, (x^n, y^n)\}
$$
Where:
- $x^i \in \mathbb{R}^d$
- $y^i \in \mathbb{R}$

Model:
$$
f : \mathbb{R}^d \rightarrow \mathbb{R}
$$
---
## 4. Loss Function (Squared Loss)

Loss of model $f$:
$$
\mathcal{L}(f) =
\frac{1}{n} \sum_{i=1}^{n}
\left( f(x^i) - y^i \right)^2
$$
Properties:
- Always non-negative
- $\mathcal{L}(f) = 0$ if and only if $f(x^i) = y^i$ for all $i$

Learning algorithm goal:
$$
\min_f \mathcal{L}(f)
$$
---
## 5. Linear Parameterization

Most common regression model:
$$
f(x) = w^T x + b
$$
Expanded form:
$$
f(x) = \sum_{j=1}^{d} w_j x_j + b
$$
Parameters:
- $w = (w_1, w_2, \dots, w_d)$
- $b$ = bias

Example (House price):
$$
f(x) =
w_1 \cdot \text{Rooms}
+
w_2 \cdot \text{Area}
+
w_3 \cdot \text{Distance}
+
b
$$
Learning algorithm finds:
$$
w, b
$$
that minimize squared loss.

---
## 6. Regression Illustration 1 (1D Example)

Assume $d = 1$.
Training data:
$$
\begin{aligned}
x &= [1, 2, 3, 6, 7] \\
y &= [2.1, 3.9, 6.2, 11.5, 13.9]
\end{aligned}
$$
Two candidate models:
Model 1:
$$
f(x) = 2x
$$
Model 2:
$$
g(x) = x + 3
$$
Predictions:
For $f$:
$$
[2, 4, 6, 12, 14]
$$
For $g$:
$$
[4, 5, 6, 9, 10]
$$
Loss of $f$:
$$
\frac{1}{5} \left[
(2-2.1)^2
+
(4-3.9)^2
+
(6-6.2)^2
+
(12-11.5)^2
+
(14-13.9)^2
\right]
$$
Loss of $g$:
$$
\frac{1}{5} \left[
(4-2.1)^2
+
(5-3.9)^2
+
(6-6.2)^2
+
(9-11.5)^2
+
(10-13.9)^2
\right]
$$
Clearly:
$$
\mathcal{L}(f) < \mathcal{L}(g)
$$
So $f$ is preferred.

---
## 7. Regression Illustration 2 (House Example)

Data:

| Rooms | Area | Distance | Price |
| ----- | ---- | -------- | ----- |
| 3     | 9    | 1.9      | 5.0   |
| 2     | 7    | 2.1      | 3.2   |
| 4     | 12   | 2.8      | 6.6   |
| 5     | 16   | 0.9      | 9.8   |
| 5     | 15   | 3.1      | 8.5   |
| 4     | 11   | 1.6      | 6.9   |
Two models:

Model $f$:
$$
f(x) = 2 \cdot \text{Rooms}
- 0.5 \cdot \text{Distance}
$$
Model $g$:
$$
g(x) =
\text{Rooms}
+
2 \cdot \text{Distance}
$$
Compute predictions for all training points.
Then compute:
$$
\mathcal{L}(f)
=
\frac{1}{n}
\sum_{i=1}^n (f(x^i) - y^i)^2
$$
$$
\mathcal{L}(g)
=
\frac{1}{n}
\sum_{i=1}^n (g(x^i) - y^i)^2
$$
We observe:
$$
\mathcal{L}(f) < \mathcal{L}(g)
$$
Hence $f$ is a better model for this dataset.

---
## Core Idea of Regression

- We are fitting a function to data.
- We choose a model family (e.g., linear).
- We define a loss function (e.g., squared loss).
- We find parameters that minimize loss.

Supervised learning = curve fitting under a loss function.

---
`***********************************************************************************`

---
## Week 1 – Lecture 4
### Supervised Learning – Classification

---
## 1. Classification Problem Setup

In classification, we predict discrete labels.

Example:
Predict whether:
$$
\text{Rooms} > 3
$$
from:
- Area
- Price
---
### Training Data

We are given:
$$
\{(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\}
$$
Where:
$$
x_i \in \mathbb{R}^d
$$
$$
y_i \in \{+1, -1\}
$$
The learning algorithm outputs:
$$
f : \mathbb{R}^d \rightarrow \{+1, -1\}
$$
---
## 2. Classification Loss

Ideal case:
$$
f(x_i) = y_i \quad \forall i
$$
In general, this may not hold.
We define classification loss as:
$$
\mathcal{L}(f) = \frac{1}{n} \sum_{i=1}^{n} \mathbf{1}(f(x_i) \neq y_i)
$$
Where:
$$
\mathbf{1}(A) =
\begin{cases}
1 & \text{if } A \text{ is true} \\
0 & \text{otherwise}
\end{cases}
$$
This measures:
> Fraction of misclassified training points.

---
## 3. Linear Classifier (Linear Separator)

Most common parameterization:
$$
f(x) = \operatorname{sign}(w^\top x + b)
$$
Where:
- $w \in \mathbb{R}^d$
- $b \in \mathbb{R}$

This defines a hyperplane:
$$
w^\top x + b = 0
$$
Points on one side → +1  
Points on the other side → -1  

---
## 4. Classification Illustration 1

### Dataset (d = 2)

Training points:
$$
(0,0), (1,0), (0,1)
$$
Label:
$$
+1
$$
and
$$
(4,4), (3,4), (4,3)
$$
Label:
$$
-1
$$
---
### Model 1
$$
f(x) = \operatorname{sign}(2 - x_1)
$$
Evaluate on training data:

All 6 correctly classified.
Therefore:
$$
\mathcal{L}(f) = 0
$$
---
### Model 2
$$
g(x) = \operatorname{sign}(x_1 - 2x_2)
$$
One point misclassified.
Therefore:
$$
\mathcal{L}(g) = \frac{1}{6}
$$
Since:
$$
0 < \frac{1}{6}
$$
Learning algorithm prefers:
$$
f
$$
---
## 5. Classification Illustration 2 (House Example)

Encoding:
$$
\text{Rooms} \leq 3 \rightarrow -1
$$
$$
\text{Rooms} > 3 \rightarrow +1
$$
Consider three models:

---
### Model f
$$
f(x) = \operatorname{sign}(\text{Area} - 10)
$$
Loss:
$$
\mathcal{L}(f) = 0
$$
---
### Model g
$$
g(x) = \operatorname{sign}(\text{Price} - 6)
$$
Loss:
$$
\mathcal{L}(g) = 0
$$
---
### Model h
$$
h(x) = \operatorname{sign}(\text{Price} - 9)
$$
Loss:
$$
\mathcal{L}(h) = \frac{3}{6}
$$
Thus:
- f and g are perfect on training data.
- h is not.
---
## 6. Important: Do NOT Evaluate on Training Data

Suppose we define:
$$
f(x) =
\begin{cases}
+1 & \text{if } x = (0,0) \\
+1 & \text{if } x = (1,0) \\
+1 & \text{if } x = (0,1) \\
-1 & \text{otherwise}
\end{cases}
$$
On training data:
$$
\mathcal{L}(f) = 0
$$
But this model is clearly useless.
It memorizes training points.
It will fail on new data.
This is called **overfitting**.

---
## 7. Train / Test Split

Learning process:
1. Training data → learn model.
2. Test data → evaluate model.

Never evaluate on training data.
Why?
Because:
Training loss underestimates real-world error.

Goal of ML:
Perform well on unseen data.

---
## 8. Validation Data (Model Selection)

Learning algorithm finds best model **within a chosen family**.
Example model family:
$$
f(x) = w_1 (\text{rooms}) + w_2 (\text{area}) + w_3 (\text{distance}) + b
$$
But why this family?
Why not:
$$
f(x) = a \cdot \frac{\text{area}}{\text{rooms}} + b \cdot \text{distance}^2 + c
$$
Choosing the correct model class is called:
### Model Selection

Data split:
- Training data → learn parameters
- Validation data → choose model class
- Test data → final evaluation
---
## Core Ideas of This Lecture

- Classification predicts discrete labels.
- Loss = fraction of misclassification.
- Linear classifier: $\operatorname{sign}(w^\top x + b)$.
- Never evaluate on training data.
- Use test data for evaluation.
- Use validation data for model selection.

---
`***********************************************************************************`

---
