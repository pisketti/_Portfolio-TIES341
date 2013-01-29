    
# Deducing types by hand:

## For :t fmap fmap

Begin:
```:t fmap```
```fmap :: Functor f => (a -> b) -> f a -> f b```

Deductions:
* First fmap as described above. Second using: ```(x -> y) -> f' x -> f' y```
* Type with the first parameter (which is a function (a -> b) - the second fmap that is) provided:
** f a -> f b
** Where (a -> b) matches (x -> y) -> f' x -> f' y
* Thus a matches the function (x -> y). This leaves b to match f' x -> f' y
* Now we can replace the original f a -> f b with the final result:
* f (x -> y) -> f (f' x -> f' y)

Which matches :t fmap fmap
* :: (Functor f1, Fuctor f) => f (a -> b) -> f (f1 a -> f1 b)
