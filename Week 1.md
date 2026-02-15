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
