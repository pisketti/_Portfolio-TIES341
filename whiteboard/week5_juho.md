# My first week of studying functional programming with Haskell..

I can honestly tell that I'm a Haskell beginner. No prior experience to this course.

Yes this is not a course for beginners but I'm going to take apart, none the less.

## Where I started

Here it is. http://learnyouahaskell.com/chapters

I use Ubuntu 12.04 and typed `sudo apt-get install ghc6 ghc6-prof ghc6-doc` as a first command to my shell.

Then it says:
```
enyone@rnet6:~$ ghci
GHCi, version 7.4.1: http://www.haskell.org/ghc/  :? for help
Loading package ghc-prim ... linking ... done.
Loading package integer-gmp ... linking ... done.
Loading package base ... linking ... done.
Prelude> 
```

The book told me to type:
```
Prelude> :set prompt "ghci> "
ghci> 
```

I belive it is because `ghci>` is more self-explanatory as a prompt than `Prelude>` is.

Yay! Now it can be used as a calculator as well!
```
ghci> 1+2
3
```

I hope this is not the only case when to use Haskell for anything.

## To the business

I've now read sections from 1 to 4 from learnyouahaskell.com

Some of the things I've learned:

```
ghci> min 4.4 3.2
3.2
```

```
ghci> (1 == 0)
False
```

```
ghci> let doubleMe x = x + x
ghci> doubleMe 3
6
```

```
ghci> head [5,4,3,2,1]
5
```

```
ghci> [1..20]
[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]
```

And so on... Hurry, hurry... No time to explain :)

### List comprehensions

```
ghci> [x*2 | x <- [1..10]]
[2,4,6,8,10,12,14,16,18,20]
```

### Tuples

```
ghci> fst ("Wow", "Non")
"Wow"
```

Hurry, hurry... Phew...

## And finally TIES341 (1st lecture, week 5) scope things

### Types

```
ghci> :t 5
5 :: Num a => a
```

It says that 5 is a `Num` and will allways be used (or "returned") as a `Num`

```
ghci> :t sum
sum :: Num a => [a] -> a
```

However `sum` is a function which takes a list `[]` (containing type `Num` elements) as one parameter and returns type `Num` as a result.

```
ghci> sum [1,2]
3
```

