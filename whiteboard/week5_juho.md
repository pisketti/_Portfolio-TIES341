# My first week of studying functional programming with Haskell..

I can honestly tell that I'm a Haskell beginner. No prior experience to this course.

Yes this is not a course for beginners but I'm going to take apart, none the less.

## Where I started

Here it is. http://learnyouahaskell.com/chapters
and http://www.haskell.org/haskellwiki/Learn_Haskell_in_10_minutes

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
ghci> (1 == 0)
False
```

```
ghci> min 4.4 3.2
3.2
```

```
ghci> round 5.4
5
```

Let it be...

```
ghci> let doubleMe x = x + x
ghci> doubleMe 3
6
```

Take first from a list...

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

`loop_through_list_operation | variable <- value`

```
ghci> [x*2 | x <- [1..10]]
[2,4,6,8,10,12,14,16,18,20]
```

### Tuples

Get first from a tuple (pair).

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

It says that 5 is a `Num` and will allways be used (or "returned") as a `Num` (because type `a` == `a` == `Num`)

```
ghci> :t sum
sum :: Num a => [a] -> a
```

However `sum` is a function which takes a list `[]` (containing type `Num` elements) as one parameter and returns type `Num` as a result. (type `a` == `a` == `Num`)

```
ghci> sum [1,2]
3
```

```
ghci> :t show
show :: Show a => a -> String
```

Show get whatever type `a` and returns a string (type `String`) representation of it.

### Functors

```
ghci> :t fmap
fmap :: Functor f => (a -> b) -> f a -> f b
```

Yes, fmap will take a function as a parameter `f` and calls it with (as a first parameter) every type `a` returning type `b` back.

```
ghci> fmap show [3,4,5]
["3","4","5"]
```

Every element in list will be sent to `show` and return value is set back to list. Just like `show 3` `show 4` `show 5` and so on..


...TBD
