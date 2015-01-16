### apply
`apply` is used to evaluate a function (often an anonymous one) over the margins of an array.

- It is most often used to apply a function to the rows or columns of a matrix
- It can be used with general arrays, e.g. taking the average of an array of matrices
- It is not really faster than writing a loop, but it works on one line!

---

```
> str(apply)
function (X, MARGIN, FUN, ...)
```

- `X` is an array
- `MARGIN` is an integer vector indicating which margins should be "retained".
- `FUN` is a function to be applied
- ... is for other arguments to be passed to `FUN`

---

```
> x <- matrix(rnorm(200), 20, 10)
> apply(x, 2, mean)
 [1]  0.08111992  0.06594684 -0.34388539  0.03067809
 [5]  0.23234381 -0.31984080 -0.49936770  0.12776170
 [9]  0.27691582  0.04532583
 
> apply(x, 1, sum)
 [1] -5.2854415 -5.0169737  3.3107725  4.1913069
 [5]  0.7458556  5.6669678 -2.0557854  1.7465664
 [9] -0.8982622  0.2656394  0.4424568 -0.9701773
[13]  0.8021237 -2.6125134 -0.6108685 -0.7836715
[17]  0.6139342 -4.4934506 -0.9659335 -0.1525831
```

---

###### col/row sums and means
For sums and means of matrix dimensions, we have some shortcuts.

- `rowSums` = `apply(x, 1, sum)
- `rowMeans = `apply(x, 1, mean)
- colSums` = `apply(x, 2, sum)
- `colMeans` = `apply(x, 2, mean)

The shortcut functions are *much* faster, but you won't notice inless you're using a large matrix.

---

##### Other Ways to Apply
Quantiles of the rows of a matrix

```
> x <- matrix(rnorm(200), 20, 10)
> apply(x, 1, quantile, probs = c(0.25, 0.75))
          [,1]       [,2]       [,3]       [,4]
25% -0.6551887 -0.3423574 -0.7118235 -0.7706426
75%  1.1099006  0.6525764  0.2834215  1.0162840
          [,5]       [,6]       [,7]       [,8]
25% -0.1487363 -0.6156533 -0.5461612 -0.5107013
75%  0.5257132  0.8152976  0.3639732  0.4327254
          [,9]      [,10]     [,11]      [,12]
25% -0.7887556 -0.5183409 -0.525671 0.05522787
75%  1.0204007  0.6398904  0.429950 0.89745164
         [,13]     [,14]     [,15]      [,16]
25% -0.3697586 0.2450278 0.3136848 -0.6700552
75%  0.7003077 0.8429127 0.9146789  0.3813227
          [,17]      [,18]      [,19]       [,20]
25% -0.66305477 -0.1420258 -1.4433989 -0.47609191
75%  0.06803479  0.6777702 -0.3276678  0.04700033
```

---

##### apply
Average matrix in an array

```
> a <- array(rnorm(2 * 2 * 10), c(2, 2, 10))
> apply(a, c(1, 2), mean)
           [,1]      [,2]
[1,] -0.3648206 0.1295988
[2,]  0.1262933 0.1924354

> rowMeans(a, dims = 2)
           [,1]      [,2]
[1,] -0.3648206 0.1295988
[2,]  0.1262933 0.1924354
```


