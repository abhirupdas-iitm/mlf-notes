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
