**Data Types Part 2

#### Creating vectors
The c() function (concatenate) can be used to create vectors of objects

	>x <- c(0.5, 0.6)			# numeric
	>x <- c(TRUE, FALSE)	# logical
	>x <- c(T, F) 					# logical
	>x <- c("a", "b")			# character
	>x <- c(9:29)					# integer
	>x <- c(1 + 0i, 2 + 4i)  # complex
	
Using the vector function:

	>x <- vector("numeric", length = 10)
	>x
	[1] 0 0 0 0 0 0 0 0 0 0
	
#### Mixing Objects

