### Simulation

##### Generating Random Numbers
Functions for probability distributions in R

- `rnorm`: generate random Normal variates with a given mean and standard deviation
- `dnorm`: evaluate the Normal probability density (with a given mean/SD) at a point (or vector of points)
- `pnorm`: evaluate the cumulative distribution function for a Normal distribution
- `rpois`: generate random Poisson variates with a given rate

---

##### Generating Random Numbers
Probability distibution functions usually have four functions associated with them. The functions are prefixed with a 

- `d` for density
- `r` for randon number generation
- `p` for cumulative distribution
- `q` for quantile function

---


Working with the Normal distributions requires using these four functions

```
dnorm(x, mean = 0, sd = 1, log = FALSE)
pnorm(q, mean = 0, sd = 1, lower.tail = TRUE, log.p = FALSE)
qnorm(p, mean = 0, sd = 1, lower.tail = TRUE, log.p = FALSE)
rnorm(n, mean = 0, sd = 1)
```

If Φ is the cumulative distribution for a standard Normal distribution, then pnorm(q) = Φ(q) and qnorm(p) = Φ<sup>-1</sup>(p)

---

##### Generating Random Number in R

```
> x <- rnorm(10)
> x
 [1]  0.40940184  1.68887329  1.58658843 -0.33090780 -2.28523554
 [6]  2.49766159  0.66706617  0.54132734 -0.01339952  0.51010842
> x <- rnorm(10, 20, 2)
> x
 [1] 19.67125 20.84139 19.19951 17.25958 21.97568 23.03949 19.38252
 [8] 17.49342 21.28448 19.91058
> summary(x)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  17.26   19.25   19.79   20.01   21.17   23.04 
```

---

##### Ensuring Reproducibility with Random Numbers
Use `set.seed` to get same random numbers for every simulation

```
> set.seed(1)
> rnorm(5)
[1] -0.6264538  0.1836433 -0.8356286  1.5952808  0.3295078
> rnorm(5)
[1] -0.8204684  0.4874291  0.7383247  0.5757814 -0.3053884
> set.seed(1)
> rnorm(5)
[1] -0.6264538  0.1836433 -0.8356286  1.5952808  0.3295078
```

Always set the random number seed when conduction a simulation!

---

##### Generating Poisson Date

```
> rpois(10, 1)
 [1] 0 0 1 1 2 1 1 4 1 2
> rpois(10, 2)
 [1] 4 1 2 0 1 1 0 1 4 1
> rpois(10, 20)
 [1] 19 19 24 23 22 24 23 20 11 22
 
> ppois(2, 2)  ## Cumulative distribution
[1] 0.6766764
> ppois(4, 2)
[1] 0.947347
> ppois(6, 2)
[1] 0.9954662
```
