# Functional Programming

## Lecture 1

Some good books for Haskell:

- Introduction to Haskell - Richard Bird (found [here](https://www.amazon.co.uk/Introduction-Functional-Programming-Prentice-Hall-Computer/dp/0134843460))
- Programming in Haskell - Graham Hutton (found [here](https://www.amazon.co.uk/Programming-Haskell-Graham-Hutton/dp/0521692695))

I'd check in a library though cause these are seriously expensive!

### What is a program?

A program is just a function. It takes input, and it produces output. But be careful about what a function is. 

$\sin x$ is not a function. It is simply a number in the range $-1 \geq n \geq 1$.

$\sin$ is a function.

Functions map a value onto another value. For example $square = x \mapsto x \times x$. In maths you may express this function as $square(x) = x * x$, but this

Back to $\sin$. In haskell we would define this function like this:

```haskell
sin :: Float -> Float
```

Which simply defines $\sin$ as a function that maps a Float (a decimal number) onto another Float.

How can we define functions with multiple inputs if functions can have only have one input?

```haskell
logBase :: Float -> (Float -> Float)
```

This is a function that takes the a single float and maps it onto another function:

$logBase : f \mapsto (g \mapsto h)$.

Now we have a function that takes a single input which applies the base to log function. In Haskell however we don't need the brackets. So our function would have the type of this:

```haskell
logBase :: Float -> Float -> Float
```

Sometimes you would want brackets however. If you need both inputs at the same time or need to pass in a function, you would want brackets..

```haskell
add1 :: Int -> Int -> Int
add1 a b = a + b

add2 :: (Int, Int) -> Int
add2 (a, b) = a + b

a = add1 1 (a has type Int -> Int)
a 2 -- answer is 3

b = add2 1 -- Errors

b = add2 (1,2) -- b now equals 3
```



### Lists

#### Definitions

Lists in Haskell are defined like this:

```haskell
x :: [Int] = [1,2,3,4,5]
```

Its pretty self explanatory the syntax going on here.

You can have lists of lists:

```haskell
x :: [[Int]] = [[1], [1,2,3], [2,3]]
```

The order matters.

#### List Comprehensions

This is a way of defining a list similar to set definitions of maths

```haskell
[x | x <- [1,2,3], even x]
```

This will produce a list with just 2 in. You can also add multiple inputs:

```haskell
[x + y | x <- [1,2,3], y <- [4,5,6]]
```

The output will be [6,7,8,7,8,9,8,9,10].

A use is mapping function. This takes a function and applies it to a list.

```haskell
map :: (a -> b) -> [a] -> [b]
map f xs = [f x | x <- xs]
```

The reason the types are letters and not something like Int or Float is because the types don't matter. All we need is consistency. We need the output of the inputted function to be the same as the list type (b) and we need the input of the inputted function to be the same as the types in the inputted list (a).

### Function Composition

In maths, $f(x) \circ g(x) = f(g(x))$ or, without the brackets (more haskelly), $f \circ g = f g$. in haskell we use the full stop. We need this because haskell is left associative.

```haskell
func1 :: Int -> Int
func2 :: Int -> Int

func1 func2 7 --This will error becuase func1 has been given a function as an input bit it exspected a function

(func1 . func2) 7 -- Much better
```

We can also chain function this way. Almost endlessly. We need the brackets because the in we didn't, it would run func2 7 which will return an Int. Then attempt to do a function composition with func1 and an Int