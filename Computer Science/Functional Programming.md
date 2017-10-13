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

We can also chain function this way. Almost endlessly. We need the brackets because the in we didn't, it would run func2 7 which will return an Int. Then attempt to do a function composition with func1 and an Int.

## Lecture 2

In this lecture we are going to write a function that converts an integer into a string. We shall call it convert and it will obviously have this type definition:

```haskell
convert :: Int -> String
```

If we input '1234', the output should be 'one thousand two hundred and thirty four'.

In order to start, we are going to split the problem into a smaller problem and handle numbers up to 10. This function shall be simply a map:
$$
1 \mapsto one \\
2 \mapsto two \\
3 \mapsto three \\ ... \\
9 \mapsto nine
$$
Lets write this in haskell:

```haskell
name :: Int -> String
name 1 = "one"
name 2 = "two"
name 3 = "three"
...
name 4 = "four"
```

But this is not scalable! If we wanted to do this up to 1,000,000, it would take years to write and run very slowly.

We also don't need our name function, in haskell we make `unitStrings`, a list that has zero up to and including 9. We can use the `!!` operator to select an element of the list `unitList !! 9 = "nine"`. Next we need to work out how to do up to 100. We need to be able to split a number into it's component parts. Remember that the input is an integer, that means that `7 / 2 = 3` in our program. To find the remainder, we can use mod. `7 % 2 = 1` where `%` is our mod operator. Lets look at this in haskell.

```haskell
x = mod 7 3 -- x = 1
y = div 7 3 -- y = 3

x1 = 7 `mod` 3 -- x = 1
y1 = 7 `div` 3 -- y = 3
```

Here I used the _tick_ sign to move a function that takes two inputs and made it take the "thing" before it as the first input.

So lets write out two functions. One that splits up our numbers into two digits, and the other that combines the words.

```haskell
combine :: (Int, Int) -> String
combine (t,u)
	| t == 0			= unitStrings !! u
	| t == 1			= teenStrings !! u
	| 2 <= t && u == 0	 = teenStrings !! t
	| 2 <= t && u /= 0	 = teenStrings !! t ++ "-" ++ unitStrings !! u
```

We are using guards, it will make the function = to the RHS if the LHS is true. If multiple are true, the first one will be run. If none a true, you can use `otherwise` which just equals true (so put it at the bottom). 

```haskell
split :: Int -> (Int, Int)
split n = (n `div` 10, n `mod` 10)
```

