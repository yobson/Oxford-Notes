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