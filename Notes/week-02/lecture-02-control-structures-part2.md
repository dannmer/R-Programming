## Control Structures part 2

---

##### while
While loops begin by testing a condition. If it is true, then they execute the loop body. Once the loop body is executed, the condition is tested again, and so forth.

```
count <- 0
while(count < 10) {
    print(count)
    count <- count + 1
}
```
While loops can potentially result in infinite loops if not written properly. Use with care!

---

##### while
Sometimes there will be more than one condition in the test.

```
z <- 5

while(z >= 3 && z <= 10) {
    print(z)
    coin <- rbinom(1, 1, 0.5)
    
    if(coin == 1) { ## random walk
        z <- z + 1
    } else {
        z <- z - 1
    }
}
```

Conditions are always evaluated from left to right.

---

##### repeat
Repeat iniitiates an infinite loop: these are not commonly used in statistical applications but they do have uses. The only way to exit a `repeat` loop is to call `break`.

```
x0 <- 1
tol <- 1e-8

repeat {
    x <- computeEstimate()
    
    if(abs(x1 - x) < tol) {
        break
    } else
}
```

This is a dangerous way ot write a loop since there is no guarantee it will stop. It is better to set a hard limit on the number of iterations (e.g. using a for loop) and then report whether convergence was achieved or not.

---

##### next, return
`next` is used to skip an iteration of a loop.

```
for(i in 1:100) {
    if(i <= 20) {
        ## Skip the first 20 iterations
        next
    }
    ## do something here
}
```

`return` signals that a function should exit and return a given value.