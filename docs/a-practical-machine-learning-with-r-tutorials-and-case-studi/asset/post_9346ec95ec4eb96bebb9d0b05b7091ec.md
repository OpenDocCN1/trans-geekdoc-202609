
# 3.10 A Project Using the tidyverse Package 45

calculate the rate of female survivors (note that the data frame DataWomen has already loaded in the background):

```
FemSurv=(......)
FemTotal=(...)
FemSurvRate=FemSurv/FemTotal
cat("The survival rate for women is:",FemSurvRate)
```

You could do the same for the male passengers. However, there is a shorter alternative to calculate the male survival rate (note that the data frame DataMen has been loaded in the background):

```
MaleSurvRate=mean(DataMen$Survived)
cat("The survival rate for men is:",MaleSurvRate)
```

## The survival rate for men is 0.1902

Why could the mean() command be used to calculate the survival rate directly? It is because the mean is calculated by dividing the sum of a variable by the number of observations. This is what we did explicitly when we calculated the female survival rate.

When we use the cat() command to print and compare the female and male survival rates, you can see that the survival rate for female passengers is much higher than the one for male passengers^{19}

```
cat("The survival rate for women is:",FemSurvRate, "\n"
"The survival rate for men is:",MaleSurvRate )
```

## The survival rate for women is: 0.742
## The survival rate for men is: 0.1902

The remaining question is if the difference between the two survival rates is high enough to reject the rejection of the Telegraph article that chivalry was dead in 1912?

To answer this, we need more analysis. R really shines when data are well organized, or when good data engineering is performed. With the prop.test() command, R can run a test if the survival rates for women and men differ significantly. The syntax only requires the values for four arguments:

- the number of female survivors,
- the number of male survivors,

^19}The character value "\n" creates a line break in the Console output.

# 3 Introduction to R and RStudio

- the number of total female passengers, and
- the number of total male passengers.

These values have been calculated already and stored in the R Objects Women-Surv, MenSurv, WomenTotal, and MenTotal. We can provide these values to the prop.test() grouped as two R vectors, for the survival numbers and one for the totals for women and men, respectively:

```
ModelPropFemaleVSMale-prop.test((FemSurv, MaleSurv),
                (FemTotal, MaleTotal))
```

Above, we have seen the output of the prop.test() command in an R object named ModelPropFemaleVSMale. We started the object with the name to indicate that it stores the output of a statistical model. ModelPropFemaleVSMale is a complex object. However, when we print it with the print() command, we extract only important information from the model object:

```
print(ModelPropFemaleVSMale)

## 2-sample test for equality of proportions
## continuity correction
##
## data: c(FemSurv, MaleSurv) out of c(FemTotal, MaleTotal)
## X-squared = 258, df = 1, p-value < 2e-16
## alternative hypothesis: two.sided
## 95 percent confidence interval:
## 0.4913 0.6124
## sample estimates:
## prop 1 prop 2
## 0.7528 0.6193
```

Reading the output backward, starting with the last line, allows us to develop the final result step-by-step. The last line from ModelPropFemaleVSMale object shows the different survival rates for female and male passengers. The difference between these two survival rates is around 0.55. The 95%-confidence interval ranges from 0.49 to 0.61. The probability of this difference being zero (both survival rates would be the same) is expressed by the P-value in Line 6 of the output. As the P-value shows, probability for the female and the male survival rate to be the same is almost zero.

We can summarize:

> The assertion from the Telegraph that chival was dead in 1912 during the Titanic disaster is most likely not.

# 3.11 Exercises: Working with R

Now, you should be ready to pursue another small project with minimal guidance (no Hints in the code block below). How about you analyze the different survival rates depending on passengers traveled in first, second, or third class?

First, create, based on the data frame DataAnalysis, three data frames containing only passengers in classes 1, 2, and 3, respectively. The object names followed by ... are already provided in the R code block.

Next, substitute the ... in lines 5–7 with the appropriate R code to calculate the survival rates for each of the three travel classes (note the data frame DataAnalysis has already been loaded in the background):

```
DataClass1 = ...
DataClass2 = ...
DataClass3 = ...
Class1SurvRate = ...
Class2SurvRate = ...
Class3SurvRate = ...
```

```
cat("Survival rate in class 1", Class1SurvRate)
cat("Survival rate in class 2", Class2SurvRate)
cat("Survival rate in class 3", Class3SurvRate)
```

Happy Analytics!

# 3.11 Exercises: Working with R

# Interactive Section

In this section, you will find the code to interact with.

The assertion from the Telegraph that chival was dead in 1912 during the Titanic disaster is most likely not.

# Character Type

In the first exercises, you will work with *Data Types*.

# Exercise 1:

The simplest way to use *Data Types* is to print:

```
print("This is text")
```

Your turn: Why don't you change the text?

# Exercise 2:

You can assign characters to an *R object*, and then print it:

```
Sentence="This is text stored in R object."
print(Sentence)
```

# Numerical Type

In the following exercises, you will assign numerical values to R objects.

We can assign a value to an R object using the “=\”-sign. Remembering to interpret the "="sign as “assigned to” rather than an “equal to” sign in algebra is important.

# Exercise 4:

Below you find an example of how to assign a value of 23 to a variable called A, and then add 100 to this value:

```
A=23
A=A+100
cat("R object A contains the numeric value", A)
```
