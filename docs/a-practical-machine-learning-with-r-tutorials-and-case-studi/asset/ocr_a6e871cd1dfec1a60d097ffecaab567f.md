38

3 Introduction to R and RStudio

```
DataTitanicFare=mutate(DataTitanicNarrow,
  FareIn2023Dollars=108.5*FareInPounds,
  FareInPounds=NULL(FareInPounds))
```

```
head(DataTitanicFare)
```

```
## Survived Class Sex Age FareIn2023Dollars
## #1 0 3 male 22 786.6
## #2 1 1 female 38 7734.2
## #3 1 1 female 26 859.9
## #4 1 1 female 35 5761.4
## #5 0 3 male 35 873.4
## #6 0 3 male 27 917.7
```

Note, we assign NULL to the existing variable FareInPounds, deleting it from the data frame (the assigned value NULL makes the variable nonexistent). As you can see, mutate() also allows updating and rewriting a variable with a new formula.

# 3.9.4 Linking Commands Together with Piping

Piping is a procedure that links one or more R commands. Piping pushes the output of one command as input to the following command. The pipe operator | connects the different R commands.

We will demonstrate how piping works with an example: Assume that on the data frame DataTitanic, we would like to create a new data frame DataFinalResult that contains:

+   * the variables Survived, Sex, Age, and FareInPounds
* only female passengers, and

+   * the passengers paid should be expressed in 2023 dollars in a new variable FareIn2023Dollars.

As you learned, for the first condition, you would use the select() command to select the required variables, ensuring your result contains only female passengers, you would use filter() to filter your observations for female passengers, and finally, to ensure the fare is expressed in 2023 dollars, you would use mutate() to calculate the correct fare.

As explained in Section 3.8 most R commands have the following structure with the first argument: the data arguments as the

```
Data More Arguments
command(Arg1, Arg2, Arg3, ..., ArgN)
Command Arguments Separated By Comma
```