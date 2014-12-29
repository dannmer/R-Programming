## Subsetting part 1

#### Subsetting 
##### There are a number of operators that can be used to extract subsets of R objects
- [ always returns an object the the same class as the original; can be used to select more than one element (there is one exception which will be described later)
- [[ is used to extract elements of a list or a data frame; it can only be used to extract a single element and the class of the returned object will not necessarily be a list or data frame
- $ is used to extract elements of a list or data frame by name, semantics are similar to that of [[.

##### Subsetting examples using integer and logical index
	> x <- c("a", "b", "c", "c", "d", "a")
	> x[1]
	[1] "a"
	> x[2]
	[1] "b"
	> x[1:4]
	[1] "a" "b" "c" "c"
	> x[x > "a"]
	[1] "b" "c" "c" "d"
	> u <- x > "a"
	> u
	[1] FALSE  TRUE  TRUE  TRUE  TRUE FALSE
	> x[u]
	[1] "b" "c" "c" "d"
	
##### Subsetting a matrix
###### Matrices can be subsetted in the usual way with (i,j) type indices. The rows are listed first.
	> x <- matrix(1:6, 2, 3)
	> x[1, 2]
	[1] 3
	> x[2, 1]
	[1] 2
###### Indices can also be missing
	> x[1, ]
	[1] 1 3 5
	> x[ ,2]
	[1] 3 4

###### Subsetting a single element of a matrix returns a vector of length one and not a 1 x 1 matrix. This behavior can be turned off by setting drop = FALSE. This also occurs when subsetting a single row or column of a matrix. 
	> x <- matrix(1:6, 2, 3)
	> x[1, 2]
	[1] 3
	> x[1, 2, drop = FALSE]
     [,1]
	[1,]    3