## Reading and Writing Data part 1
#### Reading Data
 There are a few principal functions reading data into R
 
- `read.table`, `read.csv` for reading tabular data, returns a data frame
- `readLines`, for reading lines of a text file
- `source`, for reading in R code files (`inverse` of `dump`)
- `dget`, for reading in R code files (`inverse` of `dput`)
- `load`, for reading in saved workspaces
- `unserialize`, for reading single R objects in binary form

---

#### Writing Data
The following functions are for writing data to files

- `write.table`
- `writeLines`
- `dump`
- `dput`
- `save`
- `serialize`

---

##### Reading Data Files with read.table
The read.table function is one of the most commonly used functions for reading data. It has a few important arguments.

-  `file`, the name of a file, or a connection
- `header`, logical indication if the file has a header line
- `sep`, a string indicating how the columns are separated, i.e. tabs, spaces, semicolons 
- `colClasses`, a character vector indicating the class of each column in the dataset (not required)
- `nrows`, the number of rows in the dataset, (not required)
- `comment.char`, a character string indicating the comment character (not required)
- `skip`, the number of lines to skip from the beginning, can be used to skip non-table part of a file
- `stringAsFactors`, should character variables be coded as factors? Defaults to TRUE.

---

##### Calling read.table
For small to modrately sized datasets, you can usually call read.table without specifying any other arguments

	data <- read.table("foo.text")

R will automatically

- skip lines that begin with a #
- figure out how many rows there are (and how much memory needs to be allocated)
- figure what type of varible is in each column of the table. Telling R these things directly makes R run faster and more efficiently
- `read.csv` is identical to `read.table` except that the default separator is a comma. 

---

##### Reading in Larger Datasets with read.table
With much larger datasets, doing the following things will make your life easier and will prevent R from choking

- Read (memorize) the help page for read.table, which contains many hints
- make a rough calculation of the memory required to store your dataset. If the dataset is larger than the amount of RAM on your computer, you can probably stop right here
- Set the `comment.char = " "` if there are no commented lines in your file
- use the `colClasses` argument. Specifying this option instead of using the default can make `read.table` run **much** faster, often twice as fast. This will let R know what type of data is in each column. In order to use this option, you have to know the class of each column in your data frame. If all of the columns are "numeric", for example, then you can just set `colClasses = "numeric"`. A quick and dirty way to figure out the classes of each column is the following:

```
initial <- read.table("datatable.txt", nrows = 100)
classes <- sapply(initial, class)
tabAll <- read.table("datatable.txt", cloClasses = classes)
```

- Set `nrows`. This doesn't make R run faster but it helps with memory usage. A mild overestimate is okay. You can use the Unix took `wc` to calculate the number of lines in a file.

---

##### Know your system
In general, when using R with larger datasets, it's useful to know a few things about your system

- How much memory is available?
- What other applications are in use?
- Are there other users logged into the same system?
- What operating system?
- Is the OS 32 or 64 bit? 

---

##### Calculating Memory Requirements
Given a data frame with 1,500,000 rows and 120 columns here are the calculations to determine how much memory is necessary to read the data into R.
1,500,000 x 120 x 8 bytes/numeric
= 1,440,000,000 bytes
= 1,440,000,000 / 2^20 bytes/MB
= 1,373.29 MB
= 1.34 GB

Actual memory requirements are usually higher.
 




	

