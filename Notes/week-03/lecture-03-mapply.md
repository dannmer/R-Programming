### mapply
`mapply` is a multivariate apply of sorts which applies a function in parallel over a set of arguments.

```
> str(mapply)
function (FUN, ..., MoreArgs = NULL, SIMPLIFY = TRUE, 
    USE.NAMES = TRUE) 
``

- `FUN` is a function to apply
- ... contains arguments to apply over
- `MoreArgs` is a list of other arguments to `FUN`.
- `SIMPLIFY` indicates whether the result should be simplified
```
---


The following is tedious to type

```
list(rep(1, 4), rep(2, 3), rep(3, 2), rep(4, 1))
```

Instead we can do

```
> mapply(rep, 1:4, 4:1)
[[1]]
[1] 1 1 1 1

[[2]]
[1] 2 2 2

[[3]]
[1] 3 3

[[4]]
[1] 4
```

---

##### Vectorizing a Function

```
> noise <- function(n, mean, sd) {
+     rnorm(n, mean, sd)
+ }
> noise(5, 1, 2)
[1]  1.159097  1.214242 -1.690337  1.511509
[5]  3.699912

> noise(1:5, 1:5, 2)
[1] -0.8030536  5.2578331  2.0327618  5.0097808
[5]  3.2232721
```

---

##### Instant Vectorization

```
> mapply(noise, 1:5, 1:5, 2)
[[1]]
[1] 1.557376

[[2]]
[1] 4.966199 3.908076

[[3]]
[1] 3.3987242 0.2076112 2.6337533

[[4]]
[1] -2.128117  4.104818  7.066191  5.892736

[[5]]
[1] 3.376451 6.894327 5.518463 4.482010 9.031955
```

---

Which is the same as

```
list(noise(1, 1, 2), noise(2, 2, 2),
     noise(3, 3, 2), noise(4, 4, 2),
     noise(5, 5, 2))
```