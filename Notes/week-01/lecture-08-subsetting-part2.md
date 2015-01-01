## Subsetting part 2

#### Subsetting Lists
	> x <- list(foo = 1:4, bar = 0.6)
	> x[1]
	$foo
	[1] 1 2 3 4

	> x[[1]]
	[1] 1 2 3 4
	> x$bar
	[1] 0.6
	> x[["bar"]]
	[1] 0.6
	> x["bar"]
	$bar
	[1] 0.6
	
###### Extracting multiple elements of a list
	> x <- list(foo = 1:4, bar = 0.6, baz = "hello")
	> x[c(1, 3)]
	$foo
	[1] 1 2 3 4

	$baz
	[1] "hello"
	
###### The \[\[ operator can be used with computed indices; $ can be used with literal names
	> x <- list(foo = 1:4, bar = 0.6, baz = "hello")
	> name <- "foo"
	> x[[name]]  ## computed index for "foo"
	[1] 1 2 3 4
	> x$name     ## element 'name' doesn't exist
	NULL
	> x$foo      ## element 'foo' does exist
	[1] 1 2 3 4
	
###### Subsetting nested elements of a list: the \[\[ operator can take an integer sequence
	> x <- list(a = list(10, 12, 14), b = c(3.14, 2.81))
	> x[[c(1, 3)]]
	[1] 14
	> x[[1]][[3]]
	[1] 14
	> x[[c(2, 1)]]
	[1] 3.14
	
###### Partial matching of names is allowed with \[\] and $. Best for command line use. The \[\[ operator doesn't do partial matching by default, need to pass the exact = FALSE argument
	> x <- list(aardvark = 1:5)
	> x$a
	[1] 1 2 3 4 5
	> x[["a"]]
	NULL
	> x[["a", exact = FALSE]]
	[1] 1 2 3 4 5
	
###### Removing NA values by creating a logical vector that is TRUE if the value is missing. 
	> x <- c(1, 2, NA, 4, NA, 5)
	> bad <- is.na(x)
	> x[!bad]
	[1] 1 2 4 5
	
###### Using complete.cases to get a subset of two or more vectors where there are values in all vectors at a given position
	> x <- c(1, 2, NA, 4, NA, 5)
	> y <- c("a", "b", NA, "d", NA, "f")
	> good <- complete.cases(x, y)
	> good
	[1]  TRUE  TRUE FALSE  TRUE FALSE  TRUE
	> x[good]
	[1] 1 2 4 5
	> y[good]
	[1] "a" "b" "d" "f"
	
###### Removing NA values from data frames
```> airquality[1:6, ]
  Ozone Solar.R Wind Temp Month Day
1    41     190  7.4   67     5   1
2    36     118  8.0   72     5   2
3    12     149 12.6   74     5   3
4    18     313 11.5   62     5   4
5    NA      NA 14.3   56     5   5
6    28      NA 14.9   66     5   6
> good <- complete.cases(airquality)
> airquality[good, ][1:6, ]
  Ozone Solar.R Wind Temp Month Day
1    41     190  7.4   67     5   1
2    36     118  8.0   72     5   2
3    12     149 12.6   74     5   3
4    18     313 11.5   62     5   4
7    23     299  8.6   65     5   7
8    19      99 13.8   59     5   8


```


	
	
	
	
	
	
	
	
	