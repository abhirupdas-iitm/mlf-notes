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
## Lecture 2
### Conditioning, Independence and Bayes Rule
### 1. Conditional Probability
#### Definition
Let $A, B \subseteq \Omega$ with $P(B) > 0$.
The conditional probability of $A$ given $B$ is
$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$$
Interpretation: Probability that $A$ occurs given that $B$ has occurred.

---
### 2. Conditional Probability Example: Double Dice Throw
#### Setup
$$
\Omega = \{1,2,3,4,5,6\}^2
$$
$$
P(A) = \frac{|A|}{36}
$$
---
#### Example 1
Find
$$
P(\text{sum} = 7 \mid \text{first} = 5)
$$
#### Numerator
Event: first = 5 and sum = 7
Only outcome:
$$
(5,2)
$$
$$
P(\text{sum}=7 \cap \text{first}=5) = \frac{1}{36}
$$
#### Denominator
First = 5:
$$
(5,1), (5,2), (5,3), (5,4), (5,5), (5,6)
$$
$$
P(\text{first}=5) = \frac{6}{36}
$$
#### Result
$$
P(\text{sum}=7 \mid \text{first}=5)
=
\frac{1/36}{6/36}
=
\frac{1}{6}
$$
---
#### Example 2

Find
$$
P(\text{first}=5 \mid \text{sum}=8)
$$
#### Numerator
First = 5 and sum = 8:
$$
(5,3)
$$
$$
P = \frac{1}{36}
$$
#### Denominator
Sum = 8:
$$
(2,6), (3,5), (4,4), (5,3), (6,2)
$$
$$
P(\text{sum}=8) = \frac{5}{36}
$$
#### Result
$$
P(\text{first}=5 \mid \text{sum}=8)
=
\frac{1/36}{5/36}
=
\frac{1}{5}
$$
---
### 3. Total Probability Law
#### Definitions
Events $B_1, B_2, \dots, B_n$ are:
##### Mutually Exclusive
$$
B_i \cap B_j = \varnothing
\quad \text{for } i \ne j
$$
##### Exhaustive
$$
B_1 \cup B_2 \cup \dots \cup B_n = \Omega
$$
---
#### Total Probability Formula

For any event $A$:
$$
P(A)
=
\sum_{i=1}^n P(A \cap B_i)
$$
Using conditioning:
$$
P(A)
=
\sum_{i=1}^n P(A \mid B_i) P(B_i)
$$
---
### 4. Total Probability Example: Two Urn Experiment
#### Setup
Urn 1: 9 white, 1 black  
Urn 2: 5 white, 5 black  

Choose urn uniformly, then pick one ball.
Define:
- $A$: white ball picked  
- $B_1$: urn 1 chosen  
- $B_2$: urn 2 chosen  

Since $B_1, B_2$ are mutually exclusive and exhaustive:
$$
P(A)
=
P(A \mid B_1) P(B_1)
+
P(A \mid B_2) P(B_2)
$$
Compute:
$$
P(B_1) = P(B_2) = \frac{1}{2}
$$
$$
P(A \mid B_1) = \frac{9}{10}
$$
$$
P(A \mid B_2) = \frac{5}{10}
$$
Result:
$$
P(A)
=
\frac{9}{10} \cdot \frac{1}{2}
+
\frac{5}{10} \cdot \frac{1}{2}
$$
---
### 5. Independence
#### Definition

Events $A$ and $B$ are independent if
$$
P(A \cap B) = P(A) P(B)
$$
Equivalent form when $P(B) > 0$:
$$
P(A \mid B) = P(A)
$$
---
#### Independence Example: Double Dice
Let:
- $A$: sum = 7  
- $B$: first = 5  
$$
P(A \cap B) = \frac{1}{36}
$$
$$
P(A) = \frac{6}{36}
$$
$$
P(B) = \frac{6}{36}
$$
$$
P(A) P(B) = \frac{6}{36} \cdot \frac{6}{36} = \frac{1}{36}
$$
Thus $A$ and $B$ are independent.
---
#### Non Independence Example

Let:
- $D$: sum = 4  
$$
P(B \cap D) = 0
$$
$$
P(B) = \frac{1}{6}
$$
$$
P(D) = \frac{3}{36}
$$
$$
P(B)P(D) \ne 0
$$
Thus $B$ and $D$ are not independent.
---
### 6. Bayes Rule
#### Derivation
From definition:
$$
P(A \mid B) = \frac{P(B \mid A) P(A)}{P(B)}
$$
Using total probability with $A$ and $A^c$:
$$
P(B)
=
P(B \mid A) P(A)
+
P(B \mid A^c) P(A^c)
$$
Thus,
$$
P(A \mid B)
=
\frac{P(B \mid A) P(A)}
{P(B \mid A) P(A) + P(B \mid A^c) P(A^c)}
$$
---
### 7. Bayes Rule Example: Urn Problem

Find:
$$
P(B_1 \mid A)
$$
Where:
- $A$: white ball picked  
- $B_1$: urn 1 chosen  

Given:
$$
P(A \mid B_1) = \frac{9}{10}
$$
$$
P(A \mid B_2) = \frac{5}{10}
$$
$$
P(B_1) = P(B_2) = \frac{1}{2}
$$
Using Bayes rule:
$$
P(B_1 \mid A)
=
\frac{ \frac{9}{10} \cdot \frac{1}{2} }
{ \frac{9}{10} \cdot \frac{1}{2} + \frac{5}{10} \cdot \frac{1}{2} }
=
\frac{9}{14}
$$
---
### 8. Bayes Rule Example: COVID Testing

Let:
- $C$: person has COVID  
- $T$: test positive  

Given:
$$
P(C) = \frac{1}{100}
$$
$$
P(T \mid C) = 0.9
$$
$$
P(T^c \mid C^c) = 0.9
$$
Thus:
$$
P(T \mid C^c) = 0.1
$$
Apply Bayes rule:
$$
P(C \mid T)
=
\frac{0.9 \cdot \frac{1}{100}}
{0.9 \cdot \frac{1}{100} + 0.1 \cdot \frac{99}{100}}
$$
Simplify:
$$
=
\frac{0.9}
{0.9 + 9.9}
\approx 0.1
$$
Key Insight:
$$
P(C \mid T) \ne P(T \mid C)
$$
Even with a 90 percent accurate test, low prevalence leads to small posterior probability.

---
### Summary

1. Conditional probability refines probability given information.
2. Total probability decomposes events over partitions.
3. Independence requires product rule.
4. Bayes rule flips conditioning.
5. Bayes rule is foundational for inference in machine learning.

---
`***********************************************************************************`

---
