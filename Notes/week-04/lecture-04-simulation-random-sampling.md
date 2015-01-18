### Random Sampling
the `sample` function draws random;y from a specified set of (scalar) objects allowing you to sample from arbitrary distributions.

```
> set.seed(1)
> sample(1:10, 4)
[1] 3 4 5 7
> sample(letters, 5)
[1] "f" "w" "y" "p" "n"
> sample(1:10)  ## permutation
 [1]  1  2  9  5  3  4  8  6  7 10
> sample(1:10)
 [1]  8  9  2  5  1 10  7  6  3  4
> sample(1:10, replace = TRUE)    ## Sample with replacement
 [1] 4 5 6 5 2 9 7 8 2 8
```

##### Simulation Summary

- Drawing samples from specific probability distributions can be done with r* functions
- Standard distributions are built in: Normal, Poisson, Binomial, Exponential, Gamma, etc.
- The `sample` function  can be used to draw random samples from arbitrary vectors
- Setting the random number generator seed via `set.seed` is critical for reproducibility