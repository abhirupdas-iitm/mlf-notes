## Lecture 1 

### Sets, Logic, Metric Spaces and Visualization  

---
## 1. Overview of This Week

In this week, we develop the mathematical tools that we will rely on throughout the course.  

We focus primarily on calculus, with an emphasis that is more geometric and visual compared to standard treatments.  

We begin with foundational concepts:

- Sets and functions  
- Mathematical notation  
- Logic  
- Graphical visualisation of functions  

---
## 2. Basic Sets

We repeatedly use the following fundamental sets.
### Real Numbers
$$
\mathbb{R}
$$
We denote by $\mathbb{R}$ the set of all real numbers.

---
### Positive Real Numbers (Including Zero)
$$
\mathbb{R}_+
$$
We define $\mathbb{R}_+$ as the set of non-negative real numbers, including $0$.

---
### Integers
$$
\mathbb{Z}
$$
We denote by $\mathbb{Z}$ the set of all integers.

---
### Non-Negative Integers
$$
\mathbb{Z}_+
$$
We define $\mathbb{Z}_+$ as the set of non-negative integers, including $0$.

---
## 3. Intervals

### Closed Interval
$$
[a,b] = \{ x \in \mathbb{R} \mid a \le x \le b \}
$$
We include both endpoints.

---
### Open Interval
$$
(a,b) = \{ x \in \mathbb{R} \mid a < x < b \}
$$
We exclude both endpoints.

---
## 4. Cartesian Products

We form higher-dimensional sets using Cartesian products.
### d-Dimensional Real Space
$$
\mathbb{R}^d = \mathbb{R} \times \mathbb{R} \times \dots \times \mathbb{R}
$$
An element of $\mathbb{R}^3$ is:
$$
(1, 2, 3)
$$
---
### d-Dimensional Box
$$
[a,b]^d = \{ x \in \mathbb{R}^d \mid x_i \in [a,b] \text{ for all } i = 1, \dots, d \}
$$
Each coordinate lies within $[a,b]$.

---
## 5. Metric Spaces

We define a metric space as a set equipped with a distance function.
### Euclidean Distance in $\mathbb{R}^d$
$$
d(x,y) = \|x - y\|
$$
Where:
$$
\|x - y\| = \sqrt{ \sum_{i=1}^{d} (x_i - y_i)^2 }
$$
This is the standard Euclidean metric.

---
### Open Ball
$$
B(x, \epsilon) = \{ y \in \mathbb{R}^d \mid d(x,y) < \epsilon \}
$$
We exclude the boundary.

---
### Closed Ball
$$
\overline{B}(x, \epsilon) = \{ y \in \mathbb{R}^d \mid d(x,y) \le \epsilon \}
$$
We include the boundary.

---
## 6. Sets and Logic

Let $V$ denote a universe.
We define:
- Union: $A \cup B$  
- Intersection: $A \cap B$  
- Complement: $A^c = V \setminus A$  

---
### De Morgan’s Laws
$$
(A \cup B)^c = A^c \cap B^c
$$
$$
(A \cap B)^c = A^c \cup B^c
$$
---
### Example

Let:
$$
V = [0,10]
$$
$$
A = [2,5]
$$
$$
B = [4,7]
$$
Then:
$$
A \cup B = [2,7]
$$
$$
A \cap B = [4,5]
$$
---
## 7. Logical Quantifiers

We use the following symbols:
- $\forall$ : for all  
- $\exists$ : there exists  
- $\Rightarrow$ : implies  
- $\Leftrightarrow$ : equivalent  

---
## 8. Sequences

A sequence is an ordered collection:
$$
x_1, x_2, \dots
$$
Where:
$$
x_i \in \mathbb{R}^d
$$
---
### Convergence

We say:
$$
\lim_{i \to \infty} x_i = x^*
$$
If:
$$
\forall \epsilon > 0, \exists N \in \mathbb{Z}_+ \text{ such that } x_n \in B(x^*, \epsilon) \text{ for all } n \ge N
$$
This means that eventually all points lie inside every $\epsilon$-ball around $x^*$.

---
## 9. Vector Spaces

A vector space $V$ satisfies:
If:
$$
u, v \in V
$$
and:
$$
\alpha, \beta \in \mathbb{R}
$$
Then:
$$
\alpha u + \beta v \in V
$$
---
### Dot Product

For $x, y \in \mathbb{R}^d$:
$$
x \cdot y = x^\top y = \sum_{i=1}^{d} x_i y_i
$$
---
### Norm
$$
\|x\|^2 = x \cdot x = \sum_{i=1}^{d} x_i^2
$$
---
### Orthogonality

We say $x$ and $y$ are orthogonal if:
$$
x^\top y = 0
$$
---
## 10. Functions

A function:
$$
f : A \to B
$$
- $A$ = domain  
- $B$ = codomain  

---
### 1-Dimensional Function
$$
f : \mathbb{R} \to \mathbb{R}
$$
Example:
$$
f(x) = x^2
$$
Graph:
$$
G_f = \{ (x, f(x)) \mid x \in \mathbb{R} \}
$$
---
### d-Dimensional Function
$$
f : \mathbb{R}^d \to \mathbb{R}
$$
Graph:
$$
G_f = \{ (x, f(x)) \mid x \in \mathbb{R}^d \}
$$
Where:
$$
G_f \subset \mathbb{R}^{d+1}
$$
---
## 11. Contour Plots (2D Functions)

For:
$$
f : \mathbb{R}^2 \to \mathbb{R}
$$
Example:
$$
f(x_1, x_2) = x_1 + x_2
$$
Contours are defined by:
$$
f(x_1, x_2) = c
$$
For various constants $c$.

---
### Another Example
$$
f(x_1, x_2) = x_1 x_2
$$
Contours form hyperbolas.

---
### Circular Example
$$
f(x_1, x_2) = x_1^2 + x_2^2
$$
Contours are circles.

---
## Summary

In this lecture, we introduced:
- Core sets and interval notation  
- Metric spaces and Euclidean distance  
- Logical operations and quantifiers  
- Sequences and convergence  
- Vector spaces, dot products and orthogonality  
- Functions and their graphical representation  
- Contour plots and heat maps  

These tools form the mathematical foundation required for the rest of the course.

---
`***********************************************************************************`

---

