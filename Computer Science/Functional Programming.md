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

## Lecture 3 - Types

Haskell is a strongly typed language. This means that if a function takes type A and you give it type B, it will just not work. It is also a statically typed, this means that type checking is done at compile time, not at run time. Haskell has algebraic types, this means that you can specify a type relatively. Example:

```haskell
Func1 :: Int -> Int -- This works - input is int, so is output

Func2 :: a -> a -- This also works, the input and output is of the same type
```

### Type Synonyms

A type synonym is a way of giving types another name. I shall show you a in built examples:

```haskell
type String = [Char]
```

Data is a way of defining new data types. This is how haskell defines bool:

```haskell
data Bool = False | True
```

This means that bool can be either true or false. True and False have no build in behaviour, it is simply text! It doesn't need any predefined behaviour.

```haskell
data Maybe a = Nothing | Just a
```

This is a way of writing functions that might have no value. The a is not a value, but another type. Maybe a can either be Nothing (like null) or Just a.

```haskell
f :: Int -> Maybe Int
f a
	| a == 0 = Nothing
	| otherwise Just a
```

Either:

```haskell
data Either a b = Left a | Right b
f :: Bool -> a -> b -> Either a b -- Example
f b a b 
	| a = Left a
	| otherwise Right b
	
f2 :: (a -> c) -> (b -> c) -> Either a b -> c
f2 a _ (Left  c) = a c
f2 _ b (Right c) = b c
```

We call types with 'a's and 'b's instead of 'Int' or 'String' parametric types.

### Defining the properties of parametric typed functions

Say we have a this quicksort function:

```haskell
quickSortInts :: [Int] -> [Int]
quickSortInts [] = []
quickSortInts (x:xs) = quickSortInts less ++ [x] ++ quickSortInts more
    where less = [n | n <- xs, n <  x]
          more = [n | n <- xs, x >= x]
```

We want to open this to any type, but it cannot be any type. It can only be applied to a type that is well ordered. So what we shall do is make a new function that applied a _type constraint_ to parametric types. In this case, we shall say the parametric type must be in the type class `Ord`.

```haskell
quickSort :: (Ord a) => [a] -> [a]
quickSort [] = []
quickSort (x:xs) = quickSort less ++ [x] ++ quickSort more
    where less = [n | n <- xs, n <  x]
          more = [n | n <- xs, x >= x]
```

So how do we add our types to type classes and define their behaviours? We use instance.

```haskell
data Pair a b = Pair a b

instance Eq (Pair a b) where
Pair x y == Pair q p = x == p && y == p
```

You can do this recursively as well! This is the instance of lists for Eq

```haskell
instance Eq a => Eq [a] where
[] == [] = True
(x:xs) ==
```



Something to note. Lets define an ordered pair:

```haskell
data UPair a = UPair a a
```

This is a definition of an ordered pair. Look how I haven't got a `b` like in the Pair definition. This is because a is a parametric type and not a value so all I'm saying is my ordered pair has two ordered values that are of the same type.

### Recursive Types

```haskell
data List a = Nil | Cons a (List a) -- This will work fine. You can use this to make trees!!!
```

## Lecture 4

### Type Inference

Haskell checks types using type inference. This means that often you dn't need to write the type definition... but do... it's beautiful. Parametric types mean that types can grow. For example:

```haskell
k =h
a = b -> e
e = c -> g
g = d -> h
b = d -> j
j = c -> k
-- Now for a function
a = b -> e
a = (d -> j) -> (c -> g)
a = (d -> (c -> k)) -> (c -> (d -> h))
a = (d -> c -> h) -> (c -> d -> h)
-- This is type of our simple function when we used complex paramaetric types.
```

### Types of errors in haskell

- Type error - checked at compile time not run time
- Run time errors (Manually triggered with `error :: String -> a`)
  - Divide by 0
  - Uncaught pattern (Don't forget your cheeky otherwise)
- The obvious syntax errors - compile time also.

### How Haskell Executes some things

```haskell
sq :: Int -> Int
sq x = x*x
```

1. $sq (3+4)$
2. $sq (7)$
3. $7 \times 7$
4. $49$

Or

1. $sq (3 + 4)$
2. $(3 + 4) \times (3+4)$
3. $7 \times (3+4)$
4. $7 \times 7$
5. $49$

The first way was eager evaluation. It does things as soon as you tell it that it can. The second was normal order evaluation. It took longer because it deferred any calculation until it was forced to do so. But this is more expensive. It is however far more supreme, especially when doing maths. Haskell instead uses lazy evaluation.

1. $sq(3+4)$
2. $let \ x = 3+4 \ in \ x \times x$
3. $let \ x = 7 \ in \ x \times x$
4. $49$

It took just as many steps as the eager evaluation but it deferred calculation until as late as it can but builds up data as interconnected trees. so as soon as one  value is evaluated to a numeric, all identical instances of that value are updated as they are pointers to the same memory address.

But sometimes you want eager evaluation. Here is why

| Step | Eager                   | Lazy/Normal Order                        |
| ---- | ----------------------- | ---------------------------------------- |
| 1    | $fact(3,1)$             | $fact(3,1)$                              |
| 2    | $fact(3-1, 3 \times 1)$ | $fact(3 - 1, 3 \times 1)$                |
| 3    | $fact(2, 3 \times 1)$   | $fact(2, 3 \times 1)$ (forces to be 2 because 0 check) |
| 4    | $fact(2,3)$             | $fact(2-1, (3\times 1) \times 2)$        |
| 5    | $fact(2-1, 3 \times 2)$ | $fact(1, (3 \times 1) \times 2)$         |
| 6    | $fact(1, 3 \times 2)$   | $fact(1-1,((3 \times 1) \times 2)\times 1)$ |
| 7    | $fact(1, 6)$            | $fact(0 , ((3 \times 1) \times 2) \times 1)$ |
| 8    | $fact(1-1, 6 \times 1)$ | $(3 \times 2) \times 1$                  |
| 9    | $fact(0, 6 \times 1)$   | $6 \times 1$                             |
| 10   | $fact(0, 6) = 6$        | 6                                        |

The two types of evaluation both took 10 steps, but one used a lot more memory as it stored the differed computations in memory before doing them. 

## Lecture 5

First a little fun

```haskell
not' :: Bool -> Bool
not' true = False
not' false = True
	where true = True
		  false = False
```

It doesn't matter if you give it a true or a false, it will return False. This is because true and false are not used for pattern matching, but instead used as variables. Because those variables are never called and because haskell is lazy, the where is never accessed. If you want to use a type, use the type.

### Recursion in lists

Often we use lists recursively. I shall use an example of a quick sort algorithm.

```haskell
quickSort :: (Ord a) => [a] -> [a]
quickSort [] = []
quickSort (x:xs) = quickSort less ++ [x] ++ quickSort more
    where less = [n | n <- xs, n <  x]
          more = [n | n <- xs, x >= x]
```

This has a pattern match (x:xs). This is where we split the first element of the list (x) and the rest of the list (xs) so we can use them in the recursive function. The function keeps spawning recursive tails until it gets to the empty list ([]).