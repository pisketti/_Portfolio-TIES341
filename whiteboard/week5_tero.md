
# Type deduction(s)

## fmap ((+) 1)

Basic type definitions:
```:t fmap```
```fmap :: Functor f => (a -> b) -> f a -> f b```

```:t ((+) 1)```
```((+) 1) :: (Num t) => t -> t```

* First param to fmap: ```t -> t``` (thus eliminated)
* Replacing since ```(a -> b)``` a can be replaced with t and b can be relaced with t
* Therefore the type of the function is: ```(Num t, Functor f) => f t -> f t```

Which matches ```:t fmap ((+) 1)```
* ```fmap ((+) 1) :: (Num t, Functor f) => f t -> f t```
