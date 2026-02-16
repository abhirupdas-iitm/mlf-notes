## Lecture 1 
### Four Fundamental Subspaces

### 1. Overview

In this lecture, we study the **four fundamental subspaces** associated with a matrix $A$.  
Given a matrix $A \in \mathbb{R}^{m \times n}$, we define:
1. Column Space $\mathcal{C}(A)$  
2. Null Space $\mathcal{N}(A)$  
3. Row Space $\mathcal{R}(A)$  
4. Left Null Space $\mathcal{N}(A^\top)$  
We analyze their definitions, geometric meaning, computation, and dimensional relationships.

---
### 2. Column Space

### 2.1 Definition

Let
$$
A = [u_1 \; u_2 \; \dots \; u_n]
$$
where $u_i$ are the columns of $A$.
We define the **column space** as
$$
\mathcal{C}(A) = \text{span}(u_1, \dots, u_n)
$$
That is,
$$
\mathcal{C}(A) = \left\{ \sum_{i=1}^{n} \alpha_i u_i \;\middle|\; \alpha_i \in \mathbb{R} \right\}
$$
Thus, $\mathcal{C}(A)$ consists of all linear combinations of the columns of $A$.

---
### 2.2 Connection to Solving $Ax = b$

We observe that:
$$
Ax = b
$$
is solvable **if and only if**
$$
b \in \mathcal{C}(A)
$$
Therefore, the column space characterizes exactly which right-hand sides $b$ admit solutions.

---
### 2.3 Example

Consider
$$
A =
\begin{bmatrix}
1 & 1 & 2 \\
2 & 1 & 3 \\
3 & 1 & 4 \\
4 & 1 & 5
\end{bmatrix}
$$
We observe:
$$
\text{col}_3 = \text{col}_1 + \text{col}_2
$$
Hence,
$$
\mathcal{C}(A) = \text{span}(\text{col}_1, \text{col}_2)
$$
Thus,
$$
\dim(\mathcal{C}(A)) = 2
$$
Even though $A$ has 3 columns, its column space is 2-dimensional inside $\mathbb{R}^4$.

---
### 3. Null Space

#### 3.1 Definition

We define the **null space** as
$$
\mathcal{N}(A) = \{ x \in \mathbb{R}^n \mid Ax = 0 \}
$$
---
### 3.2 Subspace Property

We verify subspace conditions:
If $x_1, x_2 \in \mathcal{N}(A)$:
$$
Ax_1 = 0, \quad Ax_2 = 0
$$
Then
$$
A(x_1 + x_2) = Ax_1 + Ax_2 = 0
$$
Also, for scalar $\alpha$:
$$
A(\alpha x) = \alpha Ax = 0
$$
Hence, $\mathcal{N}(A)$ is a subspace of $\mathbb{R}^n$.

---
### 3.3 Example (Same Matrix)

Since
$$
\text{col}_1 + \text{col}_2 - \text{col}_3 = 0
$$
we obtain
$$
x =
\begin{bmatrix}
1 \\
1 \\
-1
\end{bmatrix}
\in \mathcal{N}(A)
$$
Thus, $\mathcal{N}(A)$ is a line in $\mathbb{R}^3$.

---
### 3.4 Invertible Case

If $A$ is invertible:
$$
\mathcal{N}(A) = \{0\}
$$
and
$$
\mathcal{C}(A) = \mathbb{R}^n
$$
In this case, $Ax = b$ has a unique solution.
If $A$ is not invertible:
$$
x = x_p + x_n
$$
where
- $Ax_p = b$
- $Ax_n = 0$

---
### 3.5 Gaussian Elimination and Null Space

We compute null space by solving:
$$
Ax = 0
$$
After row reduction:
- Pivot columns correspond to basic variables
- Non-pivot columns correspond to free variables
Each free variable generates one basis vector of the null space.

---
### 4. Rank and Nullity

We define:
- **Rank** = number of pivot columns
- **Nullity** = number of free variables
We have:
$$
\text{rank}(A) = \dim(\mathcal{C}(A))
$$
$$
\text{nullity}(A) = \dim(\mathcal{N}(A))
$$
If $A$ has $n$ columns:
$$
\text{rank}(A) + \text{nullity}(A) = n
$$
This is the **Rank–Nullity Theorem**.

---
### 5. Row Space

#### 5.1 Definition

We define the row space as:
$$
\mathcal{R}(A) = \mathcal{C}(A^\top)
$$
Equivalently:
$$
\mathcal{R}(A) = \text{span of rows of } A
$$
---
### 5.2 Important Fact
$$
\text{column rank} = \text{row rank}
$$
Thus:
$$
\dim(\mathcal{R}(A)) = \dim(\mathcal{C}(A)) = r
$$
---
### 6. Left Null Space

#### 6.1 Definition

We define:
$$
\mathcal{N}(A^\top) = \{ y \in \mathbb{R}^m \mid A^\top y = 0 \}
$$
Equivalently:
$$
y^\top A = 0
$$
Thus, the left null space consists of all linear combinations of rows that produce the zero vector.

---
### 6.2 Dimension Relationship

For $A \in \mathbb{R}^{m \times n}$:
We know:
$$
\dim(\mathcal{C}(A)) + \dim(\mathcal{N}(A)) = n
$$
Applying the same to $A^\top$:
$$
\dim(\mathcal{C}(A^\top)) + \dim(\mathcal{N}(A^\top)) = m
$$
Since:
$$
\dim(\mathcal{C}(A^\top)) = r
$$
we obtain:
$$
\dim(\mathcal{N}(A^\top)) = m - r
$$
---
### 7. Summary of Dimensions

For $A \in \mathbb{R}^{m \times n}$ with rank $r$:

| Subspace                              | Dimension |
| ------------------------------------- | --------- |
| Column space $\mathcal{C}(A)$         | $r$       |
| Null space $\mathcal{N}(A)$           | $n - r$   |
| Row space $\mathcal{R}(A)$            | $r$       |
| Left null space $\mathcal{N}(A^\top)$ | $m - r$   |

---
### 8. Final Perspective

We conclude:
- Column space controls solvability of $Ax = b$
- Null space controls non-uniqueness of solutions
- Row space equals column space of $A^\top$
- Left null space captures row dependencies
- Rank determines dimensions of all four subspaces

These four spaces completely describe the structure of a matrix and form the backbone of linear algebra used in machine learning.

---
`***********************************************************************************`

---

