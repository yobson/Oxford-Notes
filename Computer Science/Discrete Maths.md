# Discrete Maths

## Lecture 1

### What is discrete maths?

It is a study of mathematical structures that are discrete (not continuous). They include the following:

- Finite sets
- Sets of whole numbers
- Finite networks
- Strings with finite alphabets
- And so much more.

The things we study about discrete objects:

- Counting them
- Proving logical statements about them
- Designing and writing algorithms with them.
- Measuring 

Course Aims:

- Learn the terminology for the maths and computer science that uses it
- Practice techniques for computing with discrete structures
- Learn ways to prove mathematical statement.

You can find the notes [here](https://www.cs.ox.ac.uk/teaching/courses/discretemaths/).

## Sets (again)

### Into

> A set is a unordered collection of distinct objects. The objects in a set are called elements or members

If x is in the set of A, we write $x \in A$.

If z isn't, we write $z \notin A$.

{1,2,3} = {1,1,2,2,3,3} = {3,2,1}

In order to define a set without listing the elements (useful for infinite sets), we use this notation
$$
\{x | P(x)\}
$$
Where $P(x)$ is a property that is either true or false for $x$. We would say this as "the set of elements for which property P holds."

We can also do it like this:
$$
\{ x \in A | P(x) \}
$$
This is useful if we want to *apply* $P(x)$ to a certain set. Finallty, we can use this notation:
$$
\{f(x) | P(x)\}
$$
Now time for one example of each:

1. $\{x | x \text{ is an animal with 2 legs} \} = \{\text{Humans, Monkeys,...}\}$
2. $\{ x \in \mathbb{N} | x \text{ is even} \} = \{ 2,4,6,8,... \}$
3. $\{2m | m \in \mathbb{Z}\} = \{-4,-2,0, 2,4,...\}$ 

That's enough of that.

### Useful Sets#

1. $\emptyset = \{\}$
2. $\mathbb{N} = \{0,1,2,3,4,...\}$
3. $\mathbb{N_+} = \mathbb{Z_+} = \{ 1,2,3,4,...\}$
4. $\mathbb{Z} = \{..., -2, -1, 0, 1,...\}$
5. $\mathbb{Z_n} = \{ 0,1,2,...,n-1 \}$
6. $\mathbb{Q} = \{ \frac{n}{m} | n \in \mathbb{Z} \ and \ m \in \mathbb{N_+} \}$
7. $\mathbb{R} = \text{The real Numbers}$

### Issues with sets

What if I had a set of sets? The set of sets would have to in that set. But what if I had a set defines as thus:
$$
T=\{s | \text{s is a set and s is not a member of itself }\}
$$
Now we have an issues which I shall explain in a flowchart:

```flow
start=>condition: Is T a member of the set T?
y=>operation: Then it is a member of of itself which the definition cannot allow.
n=>operation: Then then it should be in the set
con=>operation: Contradiction!


start(yes)->y
start(no)->n
y->con
n->con
```

So we have a problem. And for this reason, we say that a set cannot be in itself.

### Some more notation (subsets)

$A \subseteq B$  means that $A$ is a subset of $B$.

$A \supseteq B$ means that A is a superset of B.

 If we use this notation: $A \subset B$, we mean that A is a proper subset of B, this means that $A$ has less elements than $B$ and $\forall x \in A, x \in B$. I like to think if it as a less than sign (for the number of elements in a set) and a less than or equal to sign.

### Now for some logic

$$
A \cup B = \{ x | x \in A \ or \ x \in B\}
\\
A \cap B = \{ x | x \in A \ and \ x \in B \}
$$

The first is called union, the second, intersection.

## Lecture 2

### Algebraic Laws

- Idempotence Laws: $A \cup A = A \ and \ A\cap A = A$
- Commutativity Laws: $A \cup B = B \cup A \ and \ A \cap B = B \cup A$
- Associativity Laws: $(A \cup B) \cup C = A \cup (B \cup C) \ and \ (A \cap B) \cap C = A \cap (B \cap c)$
- Distributivity Laws: $A \cup (B \cap C) = (A \cup B) \cap (A \cup C) \ and \ A \cap (B \cup C) =  (A \cap B) \cup (A \cap C)$
- Zero and one laws: $A \cap \emptyset = \emptyset \ and \ A \cup \emptyset = A$ 

### Generalised Operations. 

$$
\bigcup^{n}_{i = 1} A_i = \{x | x \in A_i \text{ for some } i \} \ and \ \bigcap^{n}_{i = 1}A_i = \{ x | x \in A_i \text{ for all } i \}
$$

- Relative Complement: $A \setminus B = \{ x | x \in A \ and \ x \not \in B \}$

### More Algebraic Laws

- Cancellation Laws: $A \setminus A = \emptyset \ and \ A \setminus \emptyset = A$
- Involution Law
- De Morgan's Laws
- Right-distributivity



### Proving Non-Equality

To prove that $A \not = B$, we need a counter example.

Claim: The left-distributive law:
$$
A \setminus (B \cup C) = (A \setminus B) \cup (A \setminus C)
$$
is false.
$$
Let \ A = \{ 1 \} \\ Let B = \{1\} \\ Let C = \{\emptyset\} \\
LHS = \emptyset \\
RHS = \{1\} \not = LHS
$$

### Cartesian Product

$A \times B = \{ \langle a,b \rangle | a \in A \ and \ b \in B \}$ - This means that the Cartesian Product is simply every combination of the two set inputs in an ordered pair.

We can generalise it like the set operators:
$$
\times_{i = 1}^n A_i = \{ x_i \times x_2 \times x_3 \times... x_n | \ \forall x \in A_i \ \forall  \ i  \}
$$

### Cardinality

The size of a set is called cardinality. For finite sets, this is just the number of elements in the set. The cardinality is usually written ${|A| \ or \ \#A}$.

### Power sets

$\mathscr{P}(A)$ is the powerset of A which is a set of every possible subset of A. $\mathscr{P}(A) = \{ x | x \subseteq A \}$

## Lecture 2 

### Intervals

An interval s a subset $I$ of $\mathbb{R}$ with the interval property: $x,z \in I$ and $x < y < z \Rightarrow y \in I$

Intervals have a more consice notation:

- $(a,b) = \{ x \in \mathbb{R} \ |\ a < x < b \}$
- $(a,b] = \{ x \in \mathbb{R} \ | \ a < x \leq b \}$
- $(a, \infty) = \{ x \in \mathbb{R } \ | \ a < x \}$
- $(-\infty, b) = \{ x \in \mathbb{R} \ |x < b \}$
- $[a,b] = \{ x \in \mathbb{R} \ | \ a \leq x \leq b \}$
- $[a, b) = \{ x \in \mathbb{R} \ | \ a \leq x < b \}$
- $(a, b] = \{ x \in \mathbb{R} \ | \ a < x \leq b \}$

### Functions

> A function associates elements of one set with another. It consists of:
>
> - A set A called the domain
> - A set B called the codomain
> - A map which associates exactly one element of B with each element of A

We write $ f : A \to B$ to indicate that $f$ is a function with domain $A$ and codomain $B$, and $f \: a \mapsto b$ or $f(a) = b$ to indicate that f associates with a and b.

Two functions are only the same if the domain and co-domain are the same.

Sometimes we want to place a looser condition on the inputs and outputs. A partial function associates elements of one set with another. It consists of:

- A set A called the domain
- A set B called the codomain
- A map which associates exactly zero or one element of B with each element of A

Roughly speaking: a partial function may be "not defined" on some of its inputs. If we want to specify that a function isn't partial, we call it a total function.

### Properties of a Function

Let f be a function $f : A \to B$. The domain is $Dom(f)$, the codomain is $Im(f)= \{b \in B \ | \ B \text{is the codomain}\}$.

### Bijections

A bijection matches up elements of A and B

So if there is a bijection $f: A \to B$ then $|A| = |B|$ This also works the other way round.

A function is onto if for every $b \in B$, there is an element $a \in A$ which is mapped onto it.