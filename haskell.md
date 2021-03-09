
## Install Haskell

### Install Haskell on a Mac

```bash
brew install haskell-stack
```

## Compile a Haskell Program

```bash
$ stack ghc -- -o example example.hs
./example
```

Or in one line, compile and run:

```bash
stack ghc -- -o example example.hs && ./example
```

## Print a String

```hs
main = putStrLn "hello world"
```

## Reading from a File

```hs
main = do
  contents <- readFile "file.txt"
  putStrLn contents
```

## What does `deriving` do?

## Reading Command-Line Arguments

```hs
import System.Environment (getArgs)

main = do
  args <- getArgs
```

## How to get program name in Haskell

```hs
import System.Environment (getProgName)

main = do
  progName <- getProgName
```

## Defining a Function

- Function must start with lowercase letter or `_`.

```hs
f = \x -> \y -> x * y
```

This is sugared to become:

```hs
f x y = x * y
```

## Define a List

```hs
(:) 1 ((:) 2 ((:) 3 []))
```

Is unsugared form of:

```hs
[1,2,3]
```

## Define a String

```hs
(:) 'a' ((:) 'b' ((:) 'c' []))
```

```hs
"abc"
```

## Creating a List

- https://stackoverflow.com/questions/22784479/what-does-do-in-haskell

## What does `(:)` do?

```hs
(:) :: a -> [a] -> [a]
```

```hs
> 2 : [3,4]
[2,3,4]
```

It adds an element to a list.

## What does `(++)` do?

```hs
(++) :: [a] -> [a] -> [a]
(++) []     ys = ys
(++) (x:xs) ys = x : xs ++ ys
```

It concatenates two lists.

## Define Arithmetic Sequences

```hs
[1..5]
[1,3..9]
[1..]
[1,3..]
```

```hs
enumFromTo 1 5
enumFromThenTo 1 3 9
enumFrom 1
enumFromThen 1 3
```

## What does `do` do?

```hs
do
  putStrLn "one"
  putStrLn "two"
```

Is syntactic sugar for:

```hs
putStrLn "one" >>
putStrLn "two"
```

## What does `>>` do?

```hs
type Monad :: (* -> *) -> Constraint
class Applicative m => Monad m where
  ...
  (>>) :: m a -> m b -> m b
  ...
  	-- Defined in ‘GHC.Base’
infixl 1 >>
```

## Define a Subclass

```hs
class Parent a where
  ...

class Parent a => Child a where
  ...
```

## Define a Polymorphic Type

## How to do if-then-else

```hs
if x then y else z
```

Is sugar for:

```hs
case x of
  True -> y
  False -> z
```

## What does `.` do in Haskell

```hs
(.) :: (b -> c) -> (a -> b) -> a -> c’
```

## What does `&&` do in Haskell

```hs
(&&) :: Bool -> Bool -> Bool
```

## What does `||` do in Haskell

```hs
(||) :: Bool -> Bool -> Bool
```

## What does `.&.` do in Haskell

```hs
type Bits :: * -> Constraint
class Eq a => Bits a where
  (.&.) :: a -> a -> a
infixl 7 .&.
```

## What does `.|.` do in Haskell

```hs
type Bits :: * -> Constraint
class Eq a => Bits a where
  (.|.) :: a -> a -> a
infixl 7 .|.
```

## How to bitshift right in Haskell

```hs
value `shiftR` amount
```

## How to bitshift left in Haskell

```hs
value `shiftL` amount
```

## What does `<-` do?

```
do
    x <- y
    f x
y >>= \x -> f x

:info >>=
type Monad :: (* -> *) -> Constraint
class Applicative m => Monad m where
  (>>=) :: m a -> (a -> m b) -> m b
  ...
  	-- Defined in ‘GHC.Base’
infixl 1 >>
```

## What does `$` do?

`$` is basically a replacement for parentheses:

```hs
($) :: (a -> b) -> a -> b
infixr 0 $
```

## A string is shorthand for [character]

[’a’,’b’,’c’]

## What is a Monad?

## What is a TypeClass?

## How to use `let`

```hs
let (group1, rest) = splitWhen (/=x) xs
  in (x:group1) : group rest
```

is equivalent to:

```hs
(\(group1, rest) -> (x:group1) : group rest) (splitWhen (/=x) xs)
```

`let` inverts the positions of the body of the function and the argument to the function.

## How to use `where`

## How to use curly brackets

```hs
square2 x = result
  where { result = x * x; }
```

## thenIO

```hs
thenIO :: IO a -> IO b -> IO b
thenIO (IO m) k = IO (\ s -> case m s of (# new_s, _ #) -> unIO k new_s)
```

## What does `infixr` do?

## What does `infixl` do?

## Sources

- https://github.com/serodriguez68/haskell-cheat-sheet
- https://gist.github.com/caiorss/a39a48c4966355188f95cb9b0cf94b20
- https://hackage.haskell.org/package/CheatSheet-1.11/src/CheatSheet.pdf
- https://en.wikibooks.org/wiki/Haskell/Syntactic_sugar
- https://stackoverflow.com/questions/1817865/haskell-and-differences
- https://stackoverflow.com/questions/11567540/how-to-create-sub-type-class-of-type-class-in-haskell
- https://wiki.haskell.org/Keywords
