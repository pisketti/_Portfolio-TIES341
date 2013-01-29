    
# Deducing types by hand:

## fmap fmap

Begin:
```:t fmap```
```fmap :: Functor f => (a -> b) -> f a -> f b```

Deductions:
* First fmap as described above. Second using: ```(x -> y) -> f' x -> f' y```
* Type with the first parameter (which is a function (a -> b) - the second fmap that is) provided:
** f a -> f b
** Where (a -> b) matches ```(x -> y) -> f' x -> f' y```
* Thus a matches the function (x -> y). This leaves b to match ```f' x -> f' y```
* Now we can replace the original f a -> f b with the final result:
* ```f (x -> y) -> f (f' x -> f' y)```

Which matches :t fmap fmap
* ```:: (Functor f1, Fuctor f) => f (a -> b) -> f (f1 a -> f1 b)```

## (.) . (.)

Begin:
```:t (.)```
```(.) :: (b -> c) -> (a -> b) -> a -> c```

Deductions:
* Numbering as follows: (.2) .1 (.3) - due to middle one using infix syntax, it is actually the first to which the other two composition operators are provided as arguments
* Could be written as follows: ```(.) (.) (.)``` and then the order would be 1 2 3. I will refer to this all the way to the end now
** 1st: ```(.) :: (b1 -> c1) -> (a1 -> b1) -> a1 -> c1```
** 2nd: ```(.) :: (b2 -> c2) -> (a2 -> b2) -> a2 -> c2```
** 3rd: ```(.) :: (b3 -> c3) -> (a3 -> b3) -> a3 -> c3```
* First with 2nd (.) placed: ```(a1 -> b1) -> a1 -> c1``` and (b1 -> c1) corresponds to 2nd (.)
* Means: b1 = (b2 -> c2) and c1 = ```(a2 -> b2) -> a2 -> c2```
* First is now: ```(a1 -> b2 -> c2) -> a1 -> (a2 -> b2) -> a2 -> c2```
* First with 3rd placed: ```a1 -> (a2 -> b2) -> a2 -> c2``` and (a1 -> b2 -> c2) corresponds to 3rd (.)
* Means: a1 = (b3 -> c3), b2 = (a3 -> b3), c2 = a3 -> c3
* First is now: ```(b3 -> c3) -> (a2 -> b2) -> a2 -> a3 -> c3```
* First is now: ```(b3 -> c3) -> (a2 -> a3 -> b3) -> a2 -> a3 -> c3```

Which matches ```:t (.) . (.)```
* ```(.) . (.) :: (b -> c) -> (a -> a1 -> b) -> a -> a1 -> c```
* Where (d_ = deduced) d_b3 = b, d_c3 = c, d_a2 = a, d_a3 = a1

## getLine >>= print . reverse

Begin:
* ```:t getLine```
* ```getLine :: IO String```
* ```:t (>>=)```
* ```(>>=) :: Monad m => m a -> (a -> m b) -> m b
* ```:t print```
* ```print :: Show a => a -> IO ()```
* ```:t (.)
* ```(.) :: (b -> c) -> (a -> b) -> a -> c```
* ```:t reverse```
* ```reverse :: [a] -> [a]```

Deductions:
* TODO
