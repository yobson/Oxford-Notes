# Introduction to Logic

## Lecture 1

You can find the slides, lecture notes, worked examples and much much more [here](http://logicmanual.philosophy.ox.ac.uk). 

Why logic?

- Logic is the study of arguments and philosophy is based around arguments and their validity
- We can test validity rigorously
- Modern philosophy assumes knowledge of logic.
- Also used in linguistics, maths and the one true science (computer science)
- Helps us make precise and accurate distinctions
- It is also compulsory in our course

### Arguments

First some definitions

- Sentences that can be either true or false are called declarative sentences.
- An argument consists of a set of declarative sentances (the premises) and a sentence marked as the conclusion

An argument is logically (formally) valid iff there is no interpretation under which the premises are all true and the conclusion is false. For example Zeno is a tortoise. All tortoises have no teeth therefore Zeno has no teeth.

Features of a logically valid argument

- The truth of a conclusion follows from the truth of the premises independently from what the subject specific expressions mean. In the above example, it doesn't matter what a tortoise is or what teeth are.
- The truth of a conclusion follows from the truth of the premises purely in virtue of the 'form' of the arguments and independent of the assumptions.
- It's not possible that the premises of a logically valid argument are true if the conclusion is false and vice versa.
- An argument can be logically valid without true assumptions. That can be used to disprove a conclusion.

Every EU citizen can enter the US without a visa. Max is from Sweden therefore he can enter the US without a visa. This is not logically valid because it relies on the knowledge that Sweden is in the EU and that max as citizenship.

Consistency - a set of sentences are consistent iff there is at least one interpretation that makes all the sentences true.

Logical truth- A sentence is a logical truth iff it is true under any interpretation.

Contradiction - A sentence is a contradiction iff it is false under any interpretation. For example - 'Some metaphysicians who are also ethicists are not metaphysicians'

### Sets

A set is simply a collection of objects that we call elements. (Kinda...)

Sets are identical iff they have the same elements

$\{A,B\} = \{B,A\}$ and $\{B,B\} = \{B\}$

The set of all animals with kidneys is the same as the set of all animals with hearts. This is because the definition doesn't matter, only the elements inside.

The claim a is an element of S can be written $a \in S$

There is exactly one set with no elements witch is notated as $\emptyset$

$Mars \in \{d : d is a planet\}$

$\emptyset \in \{\emptyset\}$

### Relations

Because $\{A,B\} = \{B,A\}$, we need a different way of defining relations because order matters.

Ordered pairs are identical iff the first terms are equal and second.

$\langle d,e \rangle = \langle f,g \rangle$ iff  $d=f$ and $e = g $

A set is a binary relation iff it contains ordered pairs.

$\emptyset$ has nothing, therefore nothing that isn't an ordered pair and therefore it is a relation.

The following set is a binary relation:

$\{\langle A,B \rangle, \langle C,D \rangle, \langle E,F \rangle \}$

Definitions

- A binary relation is symmetric iff for all elements $\langle d,e \rangle$ in S, $\langle e, d \rangle \in S$. For example $\{\langle A,B \rangle, \langle B,A \rangle, \langle A,A \rangle\}$ is symmetric.
- A binary relation is transitive iff for all $\langle d,e \rangle$ and $\langle e,f \rangle$ in S, $\langle d,f \rangle \in S$
- A binary relation is reflexive iff for all $x \in S$, $\langle x,x \rangle \in R$
- A function is when for $\langle A,B \rangle$, there is no $\langle A,C \rangle$

## Lecture 2

Formal languages are far simper than natural languages. They have only one use which is to analyse logic. But it is still a language so it has the following properties:

- Syntax - Syntax is all about expressions, words and sentences. For example - Bertrand Russell is a Proper noun.
- Semantics is all about the meaning of expressions e.g Bertrand Russell refers to a British Philosopher. It refers to Bertrand Russell.

In English, we use quotation marks to isolate the expressions that we are referring to. This is one of the issues when using a language to analyse a language, we have to isolate the analysis from what we are analysing. For example 'Bertrand Russell' refers to Bertrand Russell.This is isolating the _use_ of the word from the _mention_ of the word.

### English vs $\mathcal{L}_1$

English has many different sorts of expressions:

- Sentences
- Connectives 'it is not the case that... and'
- Noun Phrase
- Verb Phrase

$\mathcal{L}_1$ has only expressions.

'It is not the case that Bertrand Russell Likes Logic' $\mapsto \neg P$ where $\neg$ was 'It is not the case' and $P$ is 'Bertrand Russell likes logic'. *It is convention to not bother with quotation marks around $\mathcal{L}_1$ sentences.* Lets look at some connectives in English and $\mathcal{L}_1$:

| Name        | in English | Symbol   |
| ----------- | ---------- | -------- |
| conjunction | and        | $\wedge$ |
| disjunction | or         | $\vee$   |
|             |            |          |
|             |            |          |

An $\mathcal{L}_1$ sentence is constructed from sentence letters. They are all sentences. If $\phi$ and $\psi$ are sentences of $\mathcal{L}_1$, then so are all of the results of the logic you build with them.

- $\neg \phi$
- $\phi \vee \psi$
- $\phi \wedge \psi$
- $\phi \to \psi$
- $\phi \leftrightarrow \psi$

If we don't need the brackets, just don't use them. There are some rules:

- $\wedge\ and \ \vee$ bind more strongly than $\to \ and \ \leftrightarrow$.
- $\neg$ is the strongest

> #### Recall Logical validity
>
> An argument is _logically valid_  iff there is **no** interpretation under which  _the premises are true and the conclusion false._

### $\mathcal{L}_1$ structures

We interpret sentence letters by assessing them in truth-values: Either T or F. A $\mathcal{L}_1-structure$ is an assignment of exactly 1 truth value to every sentence letter in $\mathcal{L}_1$.

- The $\mathcal{L}_1-structure$ only directly specifies truth values for P, Q, R...
- The logical connectives have fixed meanings
- These determine the truth-values of complex sentences 
- Notation $| \phi |_\mathcal{A}$ is the truth-value of $\phi$ under $\mathcal{A}$
- For all $\mathcal{L}_1$

Some truth tables (Wooooh!)

| $\phi$ | $\neg$ |
| ------ | ------ |
| T      | F      |
| F      | T      |

| $\phi$ | $\psi$ | $\phi \wedge \psi$ |
| ------ | ------ | ------------------ |
| T      | T      | T                  |
| T      | F      | F                  |
| F      | T      | F                  |
| F      | F      | F                  |

| $\phi$ | $\psi$ | $\phi \vee \psi$ |
| ------ | ------ | ---------------- |
| T      | T      | T                |
| T      | F      | T                |
| F      | T      | T                |
| F      | F      | F                |

| $\phi$ | $\psi$ | $\phi \to \psi$ |
| ------ | ------ | --------------- |
| T      | T      | T               |
| T      | F      | F               |
| F      | T      | T               |
| F      | F      | T               |

| $\phi$ | $\psi$ | $\phi \leftrightarrow \psi$ |
| ------ | ------ | --------------------------- |
| T      | T      | T                           |
| T      | F      | F                           |
| F      | T      | F                           |
| F      | F      | T                           |

An example: calculate $| \neg (P \to Q) \to (P \wedge Q) |_{\mathcal{B}}$

$|P|_{ \mathcal{B}} = T$ and $|Q| _{\mathcal{B}} = F$

| $\neg$ | (    | P    | $\to$ | Q    | )    | $\to$ | (    | P    | $\wedge$ | Q    | )    |
| ------ | ---- | ---- | ----- | ---- | ---- | ----- | ---- | ---- | -------- | ---- | ---- |
|        |      | T    |       | F    |      |       |      | T    |          | F    |      |
|        |      | T    | F     | F    |      |       |      | T    | F        | F    |      |
| T      |      | T    | F     | F    |      |       |      | T    | F        | F    |      |
| T      |      | T    | F     | F    |      | **F** |      | T    | F        | F    |      |

> Let $\Gamma$ be a set of sentences of $\mathcal{L}_1$ and $\phi$ be a sentence arranged with $\Gamma$ as a premise and $\phi$ is the conclusion. The sentence is valid iff there is no interpretation under which $\Gamma$ is true and $\phi$ is false. This is notates as $\Gamma \vDash \phi$.

You can also use a truth table backwards to show a contradiction.