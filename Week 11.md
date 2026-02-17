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
## Lecture 3
### Random Variables
### Definition
Given a probability space $(\Omega, \mathcal{F}, P)$, a random variable is a function
$$
X : \Omega \to \mathbb{R}
$$
If the range of $X$ is finite or countable, then $X$ is called a discrete random variable.
Since in all previous examples $\Omega$ was finite, any function defined on $\Omega$ is a discrete random variable.

---
### Examples of Random Variables

#### Example 1: Double Dice Throw Experiment
Sample space:
$$
\Omega = \{ (a,b) : a,b \in \{1,2,3,4,5,6\} \}
$$
Define
$$
X(a,b) = a
$$
This random variable represents the first die result.

---
#### Example 2: Sum of Dice

Define
$$
X(a,b) = a + b
$$
This random variable represents the sum of the faces.

---
#### Example 3: Double Coin Toss

Sample space:
$$
\Omega = \{ HH, HT, TH, TT \}
$$
Define $X$ as the number of heads:
$$
X(HH) = 2
$$
$$
X(HT) = 1
$$
$$
X(TH) = 1
$$
$$
X(TT) = 0
$$
---
### Probability Mass Function

For a discrete random variable $X$, the probability mass function is defined as
$$
f_X : \mathbb{R} \to [0,1]
$$
$$
f_X(x) = P(X = x)
$$
More formally,
$$
f_X(x) = P(\{ \omega \in \Omega : X(\omega) = x \})
$$
#### Properties
1. Non negativity:
$$
0 \le f_X(x) \le 1
$$
2. Total probability:
$$
\sum_{x \in \text{Range}(X)} f_X(x) = 1
$$
Proof:
$$
\sum_{x} f_X(x)
=
\sum_{x} P(\{ \omega : X(\omega)=x \})
$$
The sets $\{ \omega : X(\omega)=x \}$ are disjoint and their union equals $\Omega$, hence
$$
\sum_{x} f_X(x) = P(\Omega) = 1
$$
---
### Cumulative Distribution Function

The cumulative distribution function is defined as
$$
F_X(x) = P(X \le x)
$$
#### Properties
1. 
$$
0 \le F_X(x) \le 1
$$
  2.
$$
F_X(-\infty) = 0
$$
  3.
$$
F_X(\infty) = 1
$$
---
### Example: First Die Result

Under counting probability:
$$
P(A) = \frac{|A|}{36}
$$
Random variable:
$$
X = \text{first die result}
$$
PMF:
$$
f_X(x) =
\begin{cases}
\frac{1}{6} & x \in \{1,2,3,4,5,6\} \\
0 & \text{otherwise}
\end{cases}
$$
CDF:
For $x < 1$:
$$
F_X(x) = 0
$$
For $k \in \{1,\dots,6\}$:
$$
F_X(k) = \frac{k}{6}
$$
For $x \ge 6$:
$$
F_X(x) = 1
$$
---
### Example: Number of Heads

Double coin toss with
$$
P(A) = \frac{|A|}{4}
$$
Random variable: number of heads.
PMF:
$$
P(X=0) = \frac{1}{4}
$$
$$
P(X=1) = \frac{1}{2}
$$
$$
P(X=2) = \frac{1}{4}
$$
CDF:
$$
F_X(0) = \frac{1}{4}
$$
$$
F_X(1) = \frac{3}{4}
$$
$$
F_X(2) = 1
$$
---
### Example: Biased Dice

Suppose faces 1 to 5 are equally likely and face 6 is twice as likely.
Let
$$
P(X=1) = P(X=2) = P(X=3) = P(X=4) = P(X=5) = C
$$
$$
P(X=6) = 2C
$$
Using normalization:
$$
5C + 2C = 1
$$
$$
7C = 1
$$
$$
C = \frac{1}{7}
$$
Hence,
$$
P(X=i) = \frac{1}{7}, \quad i=1,\dots,5
$$
$$
P(X=6) = \frac{2}{7}
$$
---
### Indicator Random Variables

For an event $A$, define
$$
X(\omega) = \mathbf{1}_{A}(\omega)
$$
$$
X(\omega) =
\begin{cases}
1 & \omega \in A \\
0 & \text{otherwise}
\end{cases}
$$
PMF:
$$
P(X=1) = P(A)
$$
$$
P(X=0) = 1 - P(A)
$$
Example: Double coin toss.
Let $A$ be the event two heads occur.
Then
$$
P(X=1) = P(HH)
$$
$$
P(X=0) = 1 - P(HH)
$$
---
### Functions of Random Variables

If $X$ is a random variable and $g : \mathbb{R} \to \mathbb{R}$, then
$$
Y = g(X)
$$
is also a random variable.
Example:
Double dice throw.
$$
X = \text{first die result}
$$
Define
$$
Y = |X - 2|
$$
Compute PMF:
$$
P(Y=0) = P(X=2) = \frac{1}{6}
$$
$$
P(Y=1) = P(X=1 \text{ or } X=3) = \frac{2}{6}
$$
Similarly for other values.

---
### Summary

A discrete random variable is a function from $\Omega$ to $\mathbb{R}$.
Key tools:
- Probability mass function
- Cumulative distribution function
- Indicator random variables
- Functions of random variables
These form the foundation for further analysis including expectation, variance and advanced probabilistic models.

---
`***********************************************************************************`

---
## Lecture 4
### Expectation and Variance
### Expectation
#### Definition
Let $X : \Omega \to \mathbb{R}$ be a discrete random variable with probability mass function $f_X$.
The expectation of $X$ is defined as
$$
E[X] = \sum_{x \in \mathrm{Range}(X)} x f_X(x)
$$
This is a weighted average of all possible values of $X$.
#### Interpretation
Expectation represents the center of mass of the probability mass function.

---
### Examples of Expectation
#### Example 1: Single Dice Throw
Let $X$ be the face value of a fair dice.
$$
f_X(x) = \frac{1}{6}, \quad x \in \{1,2,3,4,5,6\}
$$
Then
$$
E[X] = \frac{1}{6}(1+2+3+4+5+6) = 3.5
$$
---
#### Example 2: Double Dice Throw
Let $X$ be the sum of two fair dice.
Possible values:
$$
2,3,4,5,6,7,8,9,10,11,12
$$
PMF:
$$
f_X(2)=\frac{1}{36}, \quad f_X(3)=\frac{2}{36}, \dots, f_X(7)=\frac{6}{36}, \dots, f_X(12)=\frac{1}{36}
$$
Then
$$
E[X] = \sum_x x f_X(x) = 7
$$
---
#### Example 3: Absolute Difference of Two Dice

Let $Y = |D_1 - D_2|$.
PMF:
$$
f_Y(0)=\frac{6}{36}
$$
$$
f_Y(1)=\frac{10}{36}
$$
$$
f_Y(2)=\frac{8}{36}
$$
$$
f_Y(3)=\frac{6}{36}
$$
$$
f_Y(4)=\frac{4}{36}
$$
$$
f_Y(5)=\frac{2}{36}
$$
Expectation:
$$
E[Y] = \frac{6}{36}0 + \frac{10}{36}1 + \frac{8}{36}2 + \frac{6}{36}3 + \frac{4}{36}4 + \frac{2}{36}5
$$
$$
E[Y] = \frac{70}{36}
$$
---
### Conditional Expectation
#### Conditional PMF
Let $A \subseteq \Omega$ be an event.
The conditional PMF is
$$
f_{X|A}(x) = P(X = x \mid A)
$$
#### Conditional Expectation
$$
E[X \mid A] = \sum_{x \in \mathrm{Range}(X)} x f_{X|A}(x)
$$
---
#### Example 1

Let $X$ be sum of two dice and $A$ be the event that first die equals 2.
Then
$$
f_{X|A}(3)=\frac{1}{6}, \dots, f_{X|A}(8)=\frac{1}{6}
$$
Thus
$$
E[X \mid A] = \frac{1}{6}(3+4+5+6+7+8) = 5.5
$$
---
#### Example 2

Let $A$ be the event that difference of dice equals 0.
Possible sums: $2,4,6,8,10,12$ each with probability $\frac{1}{6}$.
Then
$$
E[X \mid A] = \frac{1}{6}(2+4+6+8+10+12) = 7
$$
---
### Linearity of Expectation

For random variables $X$ and $Y$:
$$
E[X + Y] = E[X] + E[Y]
$$
For constant $a$:
$$
E[aX] = a E[X]
$$
Expectation is a linear operator.

---
#### Example: 10 Coin Toss Experiment

Let $X$ be number of heads in 10 fair coin tosses.
Define indicator variables
$$
X_i = \mathbf{1}\{\text{toss } i \text{ is head}\}
$$
Then
$$
X = \sum_{i=1}^{10} X_i
$$
By linearity:
$$
E[X] = \sum_{i=1}^{10} E[X_i]
$$
Since
$$
E[X_i] = P(\text{head}) = \frac{1}{2}
$$
Therefore
$$
E[X] = 10 \cdot \frac{1}{2} = 5
$$
---
### Variance
#### Definition
Variance of $X$:
$$
\mathrm{Var}(X) = E[(X - E[X])^2]
$$
#### Equivalent Formula
Expanding:
$$
(X - E[X])^2 = X^2 + (E[X])^2 - 2X E[X]
$$
Taking expectation:
$$
\mathrm{Var}(X) = E[X^2] - (E[X])^2
$$
---
#### Interpretation

Variance measures average squared deviation from the mean.
If $X$ is constant:
$$
\mathrm{Var}(X) = 0
$$
---
### Properties of Variance

For constant $a$:
$$
\mathrm{Var}(aX) = a^2 \mathrm{Var}(X)
$$
For random variables $X$ and $Y$:
$$
\mathrm{Var}(X + Y) = \mathrm{Var}(X) + \mathrm{Var}(Y) + 2 \mathrm{Cov}(X,Y)
$$
Variance is not linear.

---
#### Example: Variance of Dice Face

Let $X$ be face of fair dice.
$$
E[X] = 3.5
$$
Compute
$$
Y = (X - 3.5)^2
$$
Values:
$$
6.25, 2.25, 0.25, 0.25, 2.25, 6.25
$$
Thus
$$
\mathrm{Var}(X) = \frac{1}{6}(6.25 + 2.25 + 0.25 + 0.25 + 2.25 + 6.25)
$$

---
`***********************************************************************************`

---
