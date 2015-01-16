### lappy

##### Looping on the Command Line
Writing `for` and/or `while` loops is useful when programming but not particularly easy when working interactively on the command line. There are some functions which implement looping to make life easier.

- `lapply`: Loop over a list and evaluate a function on each element
- `sapply`: Same as `lapply` but tries to simplify the result
- `apply`: Apply a function over the margins of an array
- `tapply`: Apply a function over subsets of a vector
- `mapply`: multivariate version of `lapply`

An auxiliary function `split` is also useful, particularly in conjunction with `lapply`.

---

##### lapply
`lapply` takes three arguments: 

1. a list `x`
2. a function (or the name of a function) `FUN`
3. other arguments via its `...` argument

If `x` is not a list, it will be coerced to a list using `as.list()`.

```
lapply
```

The actual looping is done internally in C code.

---

`lapply` always returns a list, regardless of the class of the input.

```
x <- list(a = 1:5, b = rnorm(10))
lapply(x, mean)
```

---

```
x <- list(a = 1:4, b = rnorm(10),  c = rnorm(20, 1), d = rnorm(100, 5))
lapply(x, mean)
```

---

```

```
