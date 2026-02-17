## Lecture 1
### Probability Space and Basic Probability Calculus

### Chapter 6: Probability
#### Outline
1. Discrete Random Variables  
2. Continuous Random Variables  
3. Maximum Likelihood and Advanced Topics  
This lecture focuses on the foundational concept of a **probability space**.

---
### 1. Experiment and Sample Space

#### Definition: Experiment
An experiment is a random process whose outcome is uncertain.
All probabilistic statements are defined relative to an experiment.
#### Definition: Sample Space
The sample space, denoted by $\Omega$, is the set of all elementary outcomes of an experiment.
$$
\Omega = \text{set of elementary outcomes}
$$
---
#### Example 1: Single Coin Toss
$$
\Omega = \{ H, T \}
$$
---
#### Example 2: Single Die Throw
$$
\Omega = \{1,2,3,4,5,6\}
$$
Cardinality:
$$
|\Omega| = 6
$$
---
#### Example 3: Double Coin Toss
$$
\Omega = \{HH, HT, TH, TT\}
$$
$$
|\Omega| = 4
$$
---
#### Example 4: Double Die Throw
$$
\Omega = \{1,2,3,4,5,6\} \times \{1,2,3,4,5,6\}
$$
$$
|\Omega| = 36
$$
---
#### Example 5: Card Picking Experiment

Pick one card from a standard 52 card deck.
$$
|\Omega| = 52
$$
---
### 2. Events as Sets

#### Definition: Event
An event is any subset of the sample space.
$$
A \subseteq \Omega
$$
The collection of all events of interest is denoted by $\mathcal{F}$.
For finite sample spaces:
$$
\mathcal{F} = 2^\Omega
$$
This is called the power set of $\Omega$.
Cardinality:
$$
|\mathcal{F}| = 2^{|\Omega|}
$$
---
#### Example: Coin Toss
$$
\Omega = \{H,T\}
$$
$$
\mathcal{F} = \{\varnothing, \{H\}, \{T\}, \{H,T\}\}
$$
---
### 3. Probability Space

A probability space is defined as:
$$
(\Omega, \mathcal{F}, P)
$$
Where:
- $\Omega$ is the sample space  
- $\mathcal{F}$ is a sigma algebra of events  
- $P : \mathcal{F} \to [0,1]$ is a probability measure  
---
### 4. Probability Measure

#### Definition
A probability measure is a function:
$$
P : \mathcal{F} \to [0,1]
$$
that assigns a number between 0 and 1 to every event.

---
### 5. Axioms of Probability

#### Axiom 1
$$
P(\Omega) = 1
$$
---
#### Axiom 2
$$
P(A) \ge 0 \quad \forall A \in \mathcal{F}
$$
---
#### Axiom 3: Additivity

If $A_1, A_2, \dots, A_n$ are disjoint events, then
$$
P(A_1 \cup A_2 \cup \dots \cup A_n)
=
P(A_1) + P(A_2) + \dots + P(A_n)
$$
---
### 6. Examples of Probability Measures

#### Example 1: Fair Coin
$$
P(\varnothing) = 0
$$
$$
P(\{H\}) = P(\{T\}) = 0.5
$$
$$
P(\Omega) = 1
$$
Additivity check:
$$
P(\{H,T\}) = P(\{H\}) + P(\{T\}) = 1
$$
---
#### Example 2: Equal Probability on Double Coin Toss
$$
\Omega = \{HH,HT,TH,TT\}
$$
Define:
$$
P(A) = \frac{|A|}{4}
$$
Properties:
$$
P(\varnothing) = 0
$$
$$
P(\Omega) = 1
$$
For example:
$$
P(\{HH,HT,TT\}) = \frac{3}{4}
$$
---
#### Example 3: Double Die Throw
$$
P(A) = \frac{|A|}{36}
$$
---
#### Example 4: Degenerate Probability

Define:
$$
P(A) =
\begin{cases}
1 & \text{if } HH \in A \\
0 & \text{otherwise}
\end{cases}
$$
This corresponds to a deterministic experiment where outcome is always $HH$.

---
### 7. Basic Probability Calculus

#### Complement Rule
$$
P(A^c) = 1 - P(A)
$$
---
#### Union Rule
$$
P(A \cup B)
=
P(A) + P(B) - P(A \cap B)
$$
---
### 8. Inclusion Exclusion Principle

For three events:
$$
P(A \cup B \cup C)
=
P(A) + P(B) + P(C)
- P(A \cap B)
- P(A \cap C)
- P(B \cap C)
+ P(A \cap B \cap C)
$$
---
#### General Form

For $A_1, \dots, A_n$:
$$
P\left(\bigcup_{i=1}^n A_i\right)
=
\sum_i P(A_i)
-
\sum_{i<j} P(A_i \cap A_j)
+
\sum_{i<j<k} P(A_i \cap A_j \cap A_k)
-
\dots
+
(-1)^{n-1}
P(A_1 \cap \dots \cap A_n)
$$
---
### 9. Equal Probability Measure

Special case:
$$
P(A) = \frac{|A|}{|\Omega|}
$$
Probability reduces to counting.

---
### 10. Counting Example: Double Die Throw

Find probability that sum equals 6.
Favorable outcomes:
$$
(1,5), (2,4), (3,3), (4,2), (5,1)
$$
Total outcomes: 36
$$
P(\text{sum} = 6) = \frac{5}{36}
$$
---
### 11. Counting Example: Banana Letters

Letters: B, A, N, A, N, A
Randomly permute all 6 letters.
$$
|\Omega| = 6!
$$
Event: first three letters are A, A, A
Favorable arrangements:
$$
3! \cdot 3!
$$
Probability:
$$
P(\text{AAA}) = \frac{3! \cdot 3!}{6!}
$$
---
### Summary

A probability space consists of:
$$
(\Omega, \mathcal{F}, P)
$$
where
- $\Omega$ is the sample space  
- $\mathcal{F}$ is a collection of subsets of $\Omega$  
- $P$ is a function mapping events to values in $[0,1]$ satisfying the axioms of probability  

This forms the foundation for all subsequent concepts in probability and machine learning.

---
`***********************************************************************************`

---
