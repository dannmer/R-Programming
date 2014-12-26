**Data Types Part 1**

##### Five basic or atomic classes of objects
	- character
	- numeric
	- integer
	- complex
	- logical (True/False)
	
##### Vector - the most basic object
	-  can only contain objects of the same class
	-  Lists are an exception: can contain items of different classes
	-  create vectors with the vector() function

##### Numbers
	- treated as double precision real numbers
	- integers need to be explicitly named using an L suffix
		- Ex: enter 1L to get an integer
	- Special values
		- Inf - represents infinity and can be used in calculations: 1/Inf = 0
		- NaN - not a number, represents an undefined value, often used to indicate missing values
	 
##### Attributes
	- R objects have attributes
		- names, dimnames (dimension names)
		- dimensions: the number of rows and columns in matrices and arrays
		- class - all objects have a class
		- length - length of vector
		- can be user defined such as metadata
	- Attributes can be accessed using the attributes() function

##### Entering Input
	- Assignment operator: <-
	- when complete expression is entered at the prompt, it is evaluated and the result is returned (may be auto-printed)
	-  # character indicates a comment
		- > x <- 5             nothing is printed 
		- > x    					 auto-printing occurs
		- > print(x)          explicit printing

