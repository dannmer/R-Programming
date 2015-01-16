### split
`split` takes a vector or other objects and splits it into groups determined by a factor or a list of factors

```
> str(split)
function(x, f, drop = FALSE, ...)
```

- `x` is a vector (or list) or data frame
- `f` is a factor (or coerced to one) or a list of factors
- `drop` indicates whether empty factors levels should be dropped 


```
> x <- c(rnorm(10), runif(10), rnorm(10, 1))
> f <- gl(3, 10)
> split(x, f)
$`1`
 [1] -0.3896141  0.6876038  0.7827979 -0.6253801 -0.7395672
 [6] -0.8420623 -0.8004610 -0.3931691  0.9420184  0.2702657

$`2`
 [1] 0.2638937 0.1093291 0.8794487 0.9144800 0.7108582
 [6] 0.2642750 0.1680864 0.4124788 0.2481743 0.4629477

$`3`
 [1] -1.1925855  1.5352402  1.5502303 -0.3698097  4.2681660
 [6]  0.4307960  1.3193253  0.5747963  1.0951381  0.7238957
```

---

A common idiom is `split` followed by an `lapply`.

```
> lapply(split(x, f), mean)
$`1`
[1] -0.1107568

$`2`
[1] 0.4433972

$`3`
[1] 0.9935193
```

##### Splitting a Data Frame

```
> library(datasets)
> head(airquality)
  Ozone Solar.R Wind Temp Month Day
1    41     190  7.4   67     5   1
2    36     118  8.0   72     5   2
3    12     149 12.6   74     5   3
4    18     313 11.5   62     5   4
5    NA      NA 14.3   56     5   5
6    28      NA 14.9   66     5   6
```

--- 

```
> s <- split(airquality, airquality$Month)
> lapply(s, function(x) colMeans(x[, c("Ozone", "Solar.R", "Wind")]))
$`5`
   Ozone  Solar.R     Wind 
      NA       NA 11.62258 

$`6`
    Ozone   Solar.R      Wind 
       NA 190.16667  10.26667 

$`7`
     Ozone    Solar.R       Wind 
        NA 216.483871   8.941935 
```

---

```
> sapply(s, function(x) colMeans(x[, c("Ozone", "Solar.R", "Wind")]))
               5         6          7        8        9
Ozone         NA        NA         NA       NA       NA
Solar.R       NA 190.16667 216.483871       NA 167.4333
Wind    11.62258  10.26667   8.941935 8.793548  10.1800

> sapply(s, function(x) colMeans(x[, c("Ozone", "Solar.R", "Wind")], na.rm = TRUE))
                5         6          7          8         9
Ozone    23.61538  29.44444  59.115385  59.961538  31.44828
Solar.R 181.29630 190.16667 216.483871 171.857143 167.43333
Wind     11.62258  10.26667   8.941935   8.793548  10.18000
```

---

##### Splitting on More than One Level

```
> x <- rnorm(10)
> f1 <- gl(2, 5)
> f2 <- gl(5, 2)
> f1
 [1] 1 1 1 1 1 2 2 2 2 2
Levels: 1 2
> f2
 [1] 1 1 2 2 3 3 4 4 5 5
Levels: 1 2 3 4 5
> interaction(f1, f2)
 [1] 1.1 1.1 1.2 1.2 1.3 2.3 2.4 2.4 2.5 2.5
Levels: 1.1 2.1 1.2 2.2 1.3 2.3 1.4 2.4 1.5 2.5
```

---

Interactions can create empty levels.

```
> str(split(x, list(f1, f2)))
List of 10
 $ 1.1: num [1:2] -0.32 0.946
 $ 2.1: num(0) 
 $ 1.2: num [1:2] 0.163 -1.591
 $ 2.2: num(0) 
 $ 1.3: num -0.439
 $ 2.3: num -0.487
 $ 1.4: num(0) 
 $ 2.4: num [1:2] 1.72 -1.02
 $ 1.5: num(0) 
 $ 2.5: num [1:2] 0.436 0.424
```

---

Empty levels can be dropped.

```
> str(split(x, list(f1, f2), drop = TRUE))
List of 6
 $ 1.1: num [1:2] -0.32 0.946
 $ 1.2: num [1:2] 0.163 -1.591
 $ 1.3: num -0.439
 $ 2.3: num -0.487
 $ 2.4: num [1:2] 1.72 -1.02
 $ 2.5: num [1:2] 0.436 0.424
```


