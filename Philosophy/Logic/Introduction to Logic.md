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