# Introduction to R and RStudio

because every R package developer can design their own R object type. However, throughout this book, we will use only a few different types of R objects, and we will present some of them here.

# Objects that Store a Single Value:

R can store a single value of numerical, character, or logic in an R object by assigning the value to the object. Assigning values to R objects can be done either with a "=" or the "<-”-sign. Both are equivalent in functionality, while only the latter is correct in a mathematical sense. Nevertheless, we will use the "<-”-sign this book to assign data to R objects for simplicity.

Below are a few examples:

```
A=123.768
B=3
C="Hello World"
IsLifeGood=TRUE
```

# Vector-Objects:

In R, a vector object can store a sequence of elements of the same data type as a sequence of character, numerical, or logical values, but a mix of different Data Types in a single vector is not allowed.

The command c() (stands for combine) can be used to assign values to an R vector object. Below are a few examples related to the weather forecast for the next three days:

```
VecTemp=c(70, 68, 55)
VecWindSpeed=c("low", "low", "high")
VecIsSunny=c(TRUE, TRUE, FALSE)
```

We can use a command as mean() to calculate the mean of a vector with numerical Data Types or the command length() to calculate the number of entries in a vector:

```
MeanForeTemp=mean(VecTemp)
```

## The forecasted temperature is 64.33

> There is another more flexible R object called a list that can store a mix of Data Types in one R and even store other lists, but this is outside the scope of this introduction.