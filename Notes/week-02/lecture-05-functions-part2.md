## Functions part 2

##### Defining a function

```
f <- function(a, b = 1, c = 2, d = NULL) {
    
}
```

In addition to not specifying a default value, you can also set an argument value to `NAULL`.

---

##### Lazy Evaluation
Arguments to functions are evaluated *lazily*, so that that they are evaluated only as needed.

```
f <- function(a, b) {
    a^2
}
f(2)
```

This function never actually uses the argument `b`, so calling `f(2)` will not produce an error because the 2 gets positionally matched to `a`.

```
> f <- function(a, b) {
+     print(a)
+     print(b)
+ }
> f(45)
[1] 45
Error in print(b) : argument "b" is missing, with no default
```

Notice that "45" got printed first before the error was triggered. This is because `b` did not have to be evaluated until after `print(a)`. Once the function tried to evaluate `print(b)` it had to throw an error.

---

##### The "..." Argument
The ... argument indicates a variable number of arguments that are usually passed on to other functions.

- ... is often used when extending another function and you don't want to copy the entire argument list of the original function.

```
myplot <- function(x, y, type = "1". ...) {
    plot(x, y, type, ...)
}
```

- Generic functions use ... so that extra arguments can be passed to methods

```
> mean
function (x, ...)
UseMethod("mean")
```

The ... argument is also necessary when the number of arguments passed to the function cannot be known in advance.

```
> args(paste)
function (..., sep = " ", collapse = NULL) 


> args(cat)
function (..., file = "", sep = " ", fill = FALSE, labels = NULL, 
    append = FALSE) 
```

---

##### Arguments Coming After the "..." Argument
One catch with ... is that any argument that appear *after* ... on the argument list must be named explicitly and connot be partially matched.

```
> args(paste)
function (..., sep = " ", collapse = NULL) 

> paste("a", "b", sep = ":")
[1] "a:b"
> paste("a", "b", se = ":")
[1] "a b :"
```



























