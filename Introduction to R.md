---
title: "Introduction to R"
author: "L. K. Muthenya"
date: "3/24/2021"
output:
  pdf_document: default
  html_document: default
  word_document: default
---

## Intro to R
### First things first, we need to download and install the latest version of R and RStudio 
#### You can download the latet version of R from http://cran.r-project.org
#### RStudio can be dowloaded from http://rstudio.com/products/rstudio/download/
### The RStudio user interface (Script , Console, Environment and Plots)
#### The RStudio interface is basically divided into four windows;
- Console
- Script window
- Environment
- Plots window
#### Operations in R (+, -, *, /, ^ or **, %%)
#### R can be used to carry out basic Mathematical Operations such as;
- Addition
- Subtraction
- Multiplication
- Division
- Exponentiation, and
- Modulo arithmetic
```{r}
1 + 1
5 * 8
1 + 2 * 8 - 6 * (3 ^ 2) ## R uses algebraic logic when carrying out Mathematical Operations
5 %% 2
5/0
0/0
```
#### Exercise 1
#### Use R to calculate the following:

* 3--8
* -7+5
*$4^5$
*$\frac{1 - 1.08^{-3}}{0.08}$

### Basic Functions in R
### Understanding the general principle of functions ,i.e, name of function and the arguments in brackets
### Important to note the case sensitivity of R
### Important to note , ?function_name is very helpful in getting more info about a given function
#### ?log or help(log)

```{r}
log(1000, base = 10) ##logarithm to base 10
log(10) ##natural logarithm
exp(2)
sqrt(64)
sin(30) ##assumes the  value is in radians
cos(pi) ## 22/7 in R is pi
factorial(0)
choose(10,3)
```
#### Exercise 2

### Getting help

```{r}
help.start() ##general help page
help(function_name)
?function_name
??phrase
apropos("phrase")
```
#### Exercise 3


### The script window
#### Creating a new script
#### Running the code in the script window
#### Comments in R
#### Saving a script
#### Sourcing a script
```{r}
source('~/Project R; Introduction to R.R', echo=TRUE)

```
#### Exercise 4

###Objects in R
#### Storing data in R objects using <-
#### = can also be used but it is mainly used to assign values to variables inn functions

```{r}
a = 5
x <- 1
y <- 1:6
z <- c("one","two","three")
w <- sqrt(4)
```

#### The environment window showing the stored values
#### Using objects in commands

```{r}
a + x
a / x
sqrt(a)
```

#### Naming objects, proper conventions in R
#### IntroToR, Intro_to_R, Intro.To.R
#### Removing objects using remove(), rm() and clearing the workspace
```{r}
rm(a)

```
#### Exercise 5

### Workspaces (very important)
#### checking of current directory
#### setting of directory
#### creating a project
#### Exercise 6


### Packages
#### installing and loading packages

```{r}
install.packages("package_name")
library("package_name")
```

#### search for packages already loaded onto workspace
```{r}
search()
```

#### removing a package
```{r}
remove.packages("package_name")
```

#### Exercise 7


### Types of Data in R
#### Data in R can be;

* Numeric(Double,Integer)
* Character
* Logical
* Complex
* Raw

#### checking the type of data using the is. command and coercing using the as. command

```{r}
is.numeric(1)
is.integer(2L)
is.logical(TRUE)
is.character("actuary")

as.character(8)
as.numeric(FALSE)
```

#### Exercise 8

### Objects
#### Atomic vectors, Matrices, Arrays, Lists and Data Frames
#### Factors***

### Atomic Vectors
#### Creating Vectors

```{r}
v <- c(1,2,3,4,5,6,7,8,9,10)
is.vector(v)
class(v) ## A vector can only have only one data type. Coercion in R
str(v) ## structure of an object
seq(10)
seq(1,10,2)
u <- runif(10) ## random uniform distribution
n <- rnorm(10) ## random normal distribution
```

#### Naming Vectors
```{r}
age <- c(bob=34,larry=28,ginger=47) ## when creating the vector
claim.free <- c(3,0,8)
names(claim.free) <- c("bob","larry","ginger") ## using the names function
```

#### Indexing Vectors

```{r}
v[3] ## getting the third element in the object v
v[c(2,5)] ## getting the second and fifth element
v[4:8] ## selecting over a range
v[3:length(v)]
v[-1] ## a negative index implies selection of everything else a part from the specified ones
v[v>=4 & v<=8] ## use of logical tests to select
age["larry"] ## use of the name attribute to select an element 
```

####Vector Arithmetic
```{r}
2*v
v/2
v^2
v+v ## element by element operation
v1 <- 1:2
v + v1 ## Recycling in R; when one vector in an operation is shorter than the other
```

#### Exercise 9

### Factors
#### What is a factor? Factors are R's ways of storing categorical data
#### When creating a factor we use the factor() function
#### We use the str() function to view the levels of factors. Notice that the factors, by default, are in alphabetical order
#### You can specify the order of the factors using the level() function, though it can give varying outcome. The best would be to specify the order when creating the factor
```{r}
gender <- factor(c("male", "female", "female", "male"))
gender <- factor(c("male", "female", "female", "male"), levels = c("male", "female"))
```


#### Indexing works the same for factors
```{r}
gender[1]
```


#### Factors are character data, thus we can't apply arithmetic operations to them
```{r}
2*gender
```


### Ordered Factors
#### These are factors that follow a specific order such as the categories small, medium and large which have the following order: small < medium < large
```{r}
health <- factor(c("good", "poor", "average", "average", "good", "good"), levels = c("poor", "average", "good"), ordered = TRUE)

health[1] < health[2]
```


### Matrices
#### Matrices are created using the matrix() function
#### There are numerous ways of creating matrices:
```{r}
A <- matrix(c(3,2,4,1), nrow = 2, ncol = 2)
B <- matrix(c(3,2,4,1), nrow = 2, ncol = 2, byrow = TRUE)
```
#### Checking the properties of matrices; we can use the following functions:
```{r}
is.matrix(A)
class(A)
dim(A)
str(A)
```

#### There are other methods of creating matrices in R. These include the use of the rbind and cbind functions. For example:
```{r}
v2 <- c(1,2,3)
v3 <- c(4,5,6)

m <- cbind(v1,v2)
n <- rbind(v1,v2)
m
n
```
#### It is important to note that by default, R fills up columns first that is byRow = FALSE
#### When naming matrices we use the dimnames argument in the matrix function or the colnames and rownames functions.

```{r}
H <- matrix(c(500,100,75,750,150,100),3,2, dimnames = list(c("rent","food","bills"),c("A","B")))

H
```

```{r}
P <- matrix(c(600,75,100,525,100,150),3,2)
P

rownames(P) <- c("rent","food","bills")
colnames(P) <- c("C","D")
P
```
#### Indexing (Subsetting) Matrices
#### Since matrices have two dimensions we will need to give the row and column of the element we want. Consider a matrix M:
```{r}
M <- matrix(1:9,3,3)
M
```

```{r}
M[1,] # first row
M[,2] # second column
M[c(1,2),1] # selecting first and second row and first column
M[1:2,1:2] # selecting the all the elements in the first two rows
M[1:nrow(M),1:2] # using the nrow argument
M[-1,1] # all rows except the first one (use of negative indices)
M[M >= 1, M <= 3] # use of logical statements to subset
# Assignment; use row and column names to subset
```
#### Matrix Arithmetic
```{r}
2 * M
M - 1
M / 4
```
#### Just like in Math, you can only perform this operation on matrices of the same dimensions:
```{r}
A + B
A - M
```
#### To multiply matrices you should use the %*% operator rather than the *:
```{r}
A %*% B
```
#### Using just * multiplies the matrices on an element by element basis:
```{r}
A*B
```
#### Row and Column sums are calculated using the rowSums and colSums functions:
```{r}
rowSums(A)
colSums(A)
```
#### The transpose is obtained using the t function:
```{r}
t(A)
```
#### Other matrix Functions:
##### Determinants:
```{r}
det(A)
```
##### Inverses:
```{r}
solve(A)
```
##### Eigenvalues and Eigenvectors
```{r}
eigen(A)
eigen(A)$values # to obtain the values alone
eigen(A)$vectors # to obtain the vectors alone

```
### Arrays
#### Arrays are also a type of object in R. The array function is used to create an n-dimensional array.
#### To use array, provide an atomic vector as the first argument, and a vector of dimensions as the second argument, called dim:
```{r}
r <- array(c(1:4,41:44,81:84),dim = c(2,2,3))
r
```
### Lists
#### Lists are like atomic vectors because they are grouped into a one-dimensional set
#### Lists group together R objects such as atomic vectors, matrices and lists.
#### We use the list function to create lists:
```{r}
my_list <- list(1:50,letters[1:10], list("my","list"))
my_list
```
### Data Frames
#### Data frames are two-dimensional objects like matrices but unlike matrices, they can contain different types of data. They are by far the most useful storage structure for data analysis. Data frames group vectors into a two-dimensional table. As a result, each column of a data frame can contain a different type of data but within a column every cell must be of the same type of data. Essentially, the columns contain data for a single variable and the rows represent a single observation.
#### To create a data frame we use the data.frame function:
```{r}
my_df <- data.frame(c("Gil","Vin","Olav","Cloe"),c(21,16,40,35),c("Female","Male","Male","Female"))
my_df
```
#### To define names inside the data frame function is similar to naming elements in a vector. This is done by putting the names equal to the vectors as follows:
```{r}
my_df <- data.frame(Name = c("Gil","Vin","Olav","Cloe"),Age = c(21,16,40,35),Sex = c("Female","Male","Male","Female"))
my_df
```
#### The following can be used to check on the properties of a data frame:
```{r}
is.data.frame(my_df)
class(my_df)
nrow(my_df)
ncol(my_df)
dim(my_df)
str(my_df)
```
#### Data frames assume the observations are factors unless we tell it otherwise. Set the argument StringAsFactors = FALSE.
#### We can also create data frames from vectors:
```{r}
height <- c(186,154,166,170)
weight <- c(92,72,80,78)
B <- data.frame(height,weight)
B
str(B)
```
#### We can also create data frames using the cbind and rbind functions to combine vectors together:
#### Adding a column to a data frame using the cbind function:
```{r}
new_df <- cbind(my_df,height)
new_df
```
#### Adding a new row is more tricky. To add a new row to the data frame will require us to define a new data frame to store the data we wish to add to the data frame:
```{r}
I <- data.frame(Name = "lilo", Age = 19, Sex = "Female",height = 150)
```
#### Joining the new row to the data frame:
```{r}
new_my_df<-rbind(new_df,I)
new_my_df
```
#### Coercing and Recycling
#### Since each column of a data frame is a vector then each column must contain data of the same type. So if there is a mix of different data types in a column the R will try to coerce them all to the same type.
#### In the case of recycling, if we try to create a data frame from vectors of different lengths then the shorter vectors will be recycled:
```{r}
E <- data.frame(a1 = 1, a2 = 1:4, a3 = c(2,4))
E
```
#### However, recycling is only possible if the longest vector is a multiple of one or more of the other vectors.
```{r}
G <- data.frame(a1 = 1, a2 = 1:5, a3 = c(2,4))
G
```
#### Indexing (Subsetting) data frames
#### Since data frames have two dimensions we will need to provide the row and column of the element we want:
```{r}
new_my_df
new_my_df[1,2] # Selecting the item in the first row and the second column
new_my_df[1,] # Selecting the entire firs row
new_my_df[,2] # Selecting the entire second column
new_my_df[c(2,3),c(1,3)] # selecting multiple rows and columns
new_my_df[1:2,1:3]
new_my_df[-2,] # Selecting all the rows except the second one
```
#### It is also possible to subset a data frame using nrow and ncol:
```{r}
new_my_df[1:nrow(new_my_df),2]
new_my_df[3,2:ncol(new_my_df)]
```
#### We can also subset a data frame using the names of columns and rows:
```{r}
new_my_df[1,"Sex"]
new_my_df[3,"height"]
new_my_df[2,c("Name","Age")]
```
#### Another useful way of subsetting is using the $ notation:
```{r}
new_my_df$Name
new_my_df$height
```
#### This is a very useful way to obtain a vector object to be use in calculations.
#### Note that just like with function arguments, you can abbreviate the column name to the fewest that uniquely define it:
```{r}
new_my_df$N
new_my_df$A
```
