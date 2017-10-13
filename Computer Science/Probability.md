# Probability

## Lecture 1

Unlike the other maths lectures we have had, probability actually has application so pay attention. Having said that, we will still be setting things up in a pure maths way.

### Events and Probabilities

Consider an _experiment_ with a set of outcomes $\Omega$. We call $\Omega$ the sample space. For example, if we are tossing a coin, $\Omega = \{ H,T\}$. If we were throwing two dice, $\Omega = \{ \langle i,j \rangle | 1 \leq i, j \leq 6 \}$.

A subset of $\Omega​$ is called an event. An event $A \subseteq \Omega​$ occurs iff $w \in A​$ and $w \in \Omega​$. Events are things that we can decide have or haven't happened by looking at the outcome of our experiment. For example:

- Coming up heads: $A = \{H\}$
- Getting a total of 4: $A = \{ \langle 1,3 \rangle, \langle 2,2 \rangle, \langle 3,1 \rangle \}$

The complement of $A$ is $A^c := \Omega \neg A$ and means "Does not occur".

Some examples

- $A \cup B$ means at least one of A or B occur
- $A \cap B$ means both A and B occur.
- $A \neg B$ means  A occurs but B doesn't.

If $A \cap B = \emptyset$ we say that A and B are _disjoint_ - they cannot both occur.

We assign a probability $\mathbb{P}(A) \in [0,1]$ to each event. For example: A fair coin, $\mathbb{P} (A) = \frac{1}{2}$.

If all outcomes are equally likely, then $\mathbb{P} (A) = \frac{|A|}{|\Omega |}$.

### Elementary Combinatorics

This is the study of how many ways of arranging objects there are. Suppose we have $n$ distinguishable objects, How many ways can we order them. There are $n$ choices for the first object, then $n-1$ for the next, etc and finally 1 choice for the final object, then the number of ways to organise these objects in an order is $n(n-1)(n-2)...1 = n!$ permutations.

From all orderings of the letters in the word "FERMAT", what is the probability that we see 2 vowels followed by 4 consonants?

There are $6! = 720$ arrangements in all. There are $2! \times 4! = 48$ ways of choosing 2 vowels then 4 consonants. $\mathbb{P}(A) = \frac{48}{720} = \frac{1}{5}$.

What about arrangements when not all objects are distinguishable? If we had $A,A,A,B,C,D$, if they were all different, we would have $6!$ ways of arranging them, but $3$ are the same. We can arrange the 3 identical objects in $3!$ ways. So to see how many ways of arranging the list with non-distinguishable items is $\frac{6!}{3!}$.

The lemma is this: The number of arrangements of the n objects:

$x_1, x_1, x_1... x_1, x_2, x_2, ..., x_2 \ ... x_k, x_k, ..., x_k$, where $x_1$ appears $m_1$ times, $x_2$ appears $m_2$ times up to $x_k$ appearing $m_k$ times, we can say the multinomial coefficient is:
$$
\frac{n!}{m_1! \times m_2 ! \ ... \ m_k !}
$$
The binomial coefficient is just he multinomial coefficient for $k = 2$.

Example: How many distinct solutions are there to: $x_1 + x_2 + x_3 + x_4 + ... + x_m = n$, where $x_i \in \mathbb{Z_+}$. Lets first picture  $n$ number of balls. With variable number of dividers, how many ways can we split up the balls? In each division, $x_i$ is the number of balls. There will be _at most_ one less divider than balls, therefore the maximum number of 'objects' will be $n + m - 1$. Where $n$ gives the number of balls, and $m$ the number of dividers. The number of combinations is given by:
$$
\frac{n+m-1}{n!(m-1)!} = \begin{pmatrix} n+m-1 \\ n \end{pmatrix}
$$

## Lecture 2

Vandermonde's identity - Claim: for all $m, n, k \geq 0$,
$$
\begin{pmatrix} n+m \\ k \end{pmatrix} = \sum_{0 \leq j \leq k} \begin{pmatrix} m \\ i \end{pmatrix} \begin{pmatrix} n \\ k - j \end{pmatrix}
$$
Proof:

Imagine choosing a committee of size k from a group consisting on m undergrads and n postgrads. There are $\begin{pmatrix}m+n \\ k \end{pmatrix}$ ways to do it. Suppose we fix the no. of undergrads on the committee to be $k \in \{0,1,..,k\}$, then there are $\begin{pmatrix} m \\ j \end{pmatrix}$ ways to choose the j undergrads. And $\begin{pmatrix} n \\ k - j \end{pmatrix}$ ways to choose the $k-j$ postgrads, so  $\begin{pmatrix} m \\ i \end{pmatrix} \begin{pmatrix} n \\ k - j \end{pmatrix}$ choices overall. Sum over J to get the result.

### The Axiomatic Set-up

> A probability space is a triple $(\Omega, F, \mathbb{P})$, where:
>
> -  $\Omega$ is a set called the sample space
> -  $F$ is a collection of subsets of $\Omega$
> -  $\mathbb{P}$ is a function from $F$ to to $\mathbb{R}$ satisfying axioms $P_1 - P_3$ below.

Axioms:

- $F_1$ : $\Omega \in F$.

- $F_2$ : If $A \in F$ then $A^c \in F$.

- $F_3(a)$ : If $A, B \in F$, then$ A \cup B \in F$

- $F_3(a)$ : If $A_i \in F$ for $i = 1,2,3,...$, then $\cup_{i = 1}^{\infty}A_i \in F$.

- $P_1$ : $\mathbb{P} (A) \geq 0 \ \ \forall A \in F$

- $P_2$ : $\mathbb{P}(\Omega) = 1$

- $P_3(a)$ : If $A, B \in F$ and $A, B$ are disjoint then $\mathbb{P} (A \cup B) = \mathbb{P}(A) + \mathbb{P}(B)$

- $P_4(a)$ : If $A_i \in F$ for $i=1,2,3,...$ and $A_i \cap A_j = \emptyset$ for all $i \not = j$, then $\mathbb{P}(\cup_{i = 1}^{\infty}A_i) = \sum_{0 < i < \infty} \mathbb{P}(A_i)$


#### Examples of things we can deduce:

let $(\Omega, F, \mathbb{P}) be the probability space.$

- If $A, B \in F$, then $A \cap B \in F$
- If $A \in F$, then $\mathbb{P}(A^c) = 1- \mathbb{P}(A)$ 
- If $A \subseteq B$, then $\mathbb{P}(A) \leq \mathbb{P}(B)$



#### Size of Sets

An infinite set $S$ is countable if if it can be "put in bijection with the natural numbers", that is, it's elements can be written in a list:
$$
S = \{ x_1,x_2,x_3,... \} = \{ x_i | i \in \mathbb{N} \}
$$
Otherwise $S$ is uncountable. For example $\mathbb{N}$ and $\mathbb{Q}$ are countable but $\mathbb{R}$ is not. $P_3(b)$ talks about countable additivity.

#### Conditional Probability

> Let $A,B \in F$ with $\mathbb{P}(B) > 0$. The conditional probability of A given B is $\mathbb{P}(A|B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)}$.

Example: Roll a fair die.
$$
\Omega = \{1,2,3,4,5,6\} \\ \mathbb{P}(A) = \frac{|A|}{6} \ \forall \ A \\
Let \ A=\{6\} \\ Let \ B = \{\text{result is even}\} = \{2,4,6\} \\
So \ \mathbb{P}(B) = \frac{1}{2}, \mathbb{A} = \frac{1}{6}, also \ \mathbb{P}(A \cap B) = \frac{1}{6}. \\
So \ \mathbb{P}(A | B) = \frac{1/6}{1/2} = \frac{1}{3}.
$$
