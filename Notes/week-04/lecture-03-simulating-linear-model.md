### Simulating a Linear Model
Suppose we want to simulate from the following linear model

<p style='text-align: center;'>y = $\beta_0$ + $\beta_1 x$ + $\varepsilon$</p>

where $\varepsilon\sim\mathcal{N}(0, 2^2)$. Assume $x\sim\mathcal{N}(0,1^2)$, $\beta_0 = 0.5$ and $\beta_1 = 2$.

```
> set.seed(20)
> x <- rnorm(100)
> e <- rnorm(100, 0, 2)
> y <- 0.5 + 2 * x + e
> summary(y)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
-6.4080 -1.5400  0.6789  0.6893  2.9300  6.5050 
> plot(x, y)
```

<img src="../assets/images/image-01.png" height=500>
  
  
  

  
