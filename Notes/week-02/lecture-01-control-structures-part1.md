#### Control Structures
Control structures in R allow you to control the flow of execution of the program, depending on runtime conditions. Common structures are:

- `if`, `else`: testing a condition
- `for`: execute a loop a fixed number of times
- `while`: execute a loop *while* a condition is true
- `repeat`: execute an infinite loop
- break`: break the execution of a loop
- `next`: skip the interation of a loop
- `return`: exit a function

Most control structures are not used in interactive sessions, but rather when writing functions or longer expressions.

##### Control Structures: if
```
if(<condition>) {
    ## do something
} else {
    ## do something else
}
if(<condition1>) {
    ## do something
} else if (<condition2>) {
    ## do something different
} else {
    ## do something different
}
```