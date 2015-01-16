### tapply
`tapply` is used to apply a function over subsets of a vector. I don't know why it's called `tapply`.

```
> str(tapply)
function (X, INDEX, FUN = NULL, ..., simplify = TRUE) 
```

- `X` is a vector
- `INDEX` is a factor or a list of factors (or else they are coerced to factors)
- `FUN` is a function to be applied
- ... contains other arguments to be passed to `FUN`
- `simplify`, should we simplify the result?

---

Take group means.

```
> x <- c(rnorm(10), runif(10), rnorm(10, 1))
> f <- gl(3, 10)
> f
 [1] 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 3 3 3 3 3 3 3 3
[29] 3 3
Levels: 1 2 3
> tapply(x, f, mean)
         1          2          3 
0.02854248 0.32553982 0.52991637 
```

---

Take group means without simplification.

```
> tapply(x, f, mean, simplify = FALSE)
$`1`
[1] 0.02854248

$`2`
[1] 0.3255398

$`3`
[1] 0.5299164
```

---

Find group ranges.

```
> tapply(x, f, range)
$`1`
[1] -1.222594  1.907474

$`2`
[1] 0.00413598 0.77782591

$`3`
[1] -0.1994718  1.5419210
```

---

