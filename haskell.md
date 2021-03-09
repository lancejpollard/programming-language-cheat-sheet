
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

## Reading Command-Line Arguments

## Defining a Function

```hs
f :: Int -> Int
f x = x ^ 2
```

## Define a Subclass

## Define a Polymorphic Type

## Sources

- https://github.com/serodriguez68/haskell-cheat-sheet
- https://gist.github.com/caiorss/a39a48c4966355188f95cb9b0cf94b20
