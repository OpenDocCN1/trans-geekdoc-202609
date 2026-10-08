
most programming languages. It determines whether a given statement is supposed to be executed or not. When the statement checks for a given condition, and it's found to be true, then the set of code presented inside is executed.
The if condition computes a Boolean expression and executes the block of code only when the Boolean expression is TRUE.
Based on the syntax of the statement, the condition will be implemented to a Boolean expression (true or false). In case the condition is true, then the statement inside the if block is executed, and when the condition is false, program present inside the if block will not be implemented.
Below is the flow chart of the if statement:

![](img/43582740ac1227a817786ef73e0f3772_323_0.png)

If you look at the above flow-chart, the first controller will reach an if condition and determine whether the condition is true, then the statements will be implemented; otherwise the code within the block will be executed.

## If-else Statements
The statement itself indicates that if a given condition is found to be true then execute the statements inside if block and if the condition is false, then execute the else block.
The else block will run only when the condition becomes false; this is the block where you will execute some actions when the condition is not true.

If-else statement computes the Boolean expression and implements the block of code available inside the if block if the condition is True and executes the block of code in the else block when the condition becomes false.

The syntax is is:

If (Boolean expression):
Block of code
else:
Block of code

In this case, the condition will be executed to a Boolean expression. If the condition is found to be true, then the statements present inside the if block will be implemented and if the condition is false, then the statements inside the program will be implemented.

![](img/43582740ac1227a817786ef73e0f3772_324_0.png)

Let’s explore the above flowchart
If you observe keenly, you will notice that the first controller will reach the if condition and check whether the if condition is true, if found to be true, then the statements of the if block will be implemented otherwise, the block will be executed and later the remaining code outside the if-else block will be implemented.

## The Nested if–else Statements
The nested if-else statements refer to an if statement or if-else statement available inside another if or if-else block. Python provides this property as well; this will help us confirm multiple conditions in a given program. An if statement available inside another if statement which is present inside another if statements and so forth.

## Nested if Syntax
The syntax goes as follows:

```
If (condition):
#statements to run if the condition is true
If (condition):
#statements to execute if the condition is true
#end of nested
```

The above syntax clearly shows that the if block will feature another block in it and so forth. The if block can hold ‘n’ number of if block within. Consider the following program:

```
Number =10
if (number >0):
    print("this number is greater than 10")
if (number <10):
    print("This number is less than 10")
```

In the above example, a variable number is declared with the value of 10. First, it will confirm the first statement is true, then the block of code inside the first statement will be executed then it will determine whether the second statement is true and so on.

## Elif ladder
You have learned about the elif statements, but not the elif ladder. The name implies a program that has a ladder of elif statements structured in the form of a ladder.

```
if (condition):
    #Statements to execute if condition is true
elif (condition):
    #Statements to be executed when condition is false and elif condition is true
elif (condition):
    #Set of statements to be executed when both if and first elif condition
is false and second elif condition is true
elif (condition):

#Set of statements to be executed when if, first elif and second elif
conditions are false and third elif statement is true

else:
    #Set of statement to be executed when all if and elif conditions are
false
```
statement is handy when you want to test multiple expressions.

## Example of elif ladder
my_marks = 89

```
if (my_marks < 35):
    print("Sorry!!! You are failed in the exam")
```

```
elif(my_marks < 60): print("Passed in Second class") 
elif(my_marks > 60 and my_marks < 85):
    print("Passed in First class")
```

```
else:
    print("Passed in First class with distinction")
```

This program demonstrates the elif ladder. First, the control enters the if statement and determines the condition if it is true, if found to be true, then the set of statements inside the if block will be implemented it will be skipped and the controller will come to the first elif block and compute the condition.

The same process will proceed for all the remaining elif statements and in case all if and elif conditions are found to be false then the else block will be executed.

## The if-else in a Single Line
In Python, it's still possible to write statements and elif statements in a single line without fearing the indentation.

## If Statement in a Single Line
We know we can write statements as indicated below:

If (condition):
#set of statements to implement if condition is true

In Python, it is okay to write the above block of code in a single line.
For example:

If (condition): statement 1; statement 2; statement 3; ...statement n
In case the condition is true, then execute statement 1, statement 2, and so forth.

However, if the condition is false, then none of the statements will be executed.

## elif statements in a single line
syntax
if(condition):
#set of statement to implement if it’s true
elif(condition1):
#set of statements to run if the condition is true
Else:
#set of statements to run if condition and condition1 is false

This block can still be written as shown below:
Syntax:

```
if (condition): #Set of statement to execute if condition is true
elif (condition1): #Set of statement to execute if condition1 is true
else: #Set of statement to execute if condition and condition1 is true
```

There can be different statements as you simply need to
Syntax:

```
if (condition): statement 1; statement 2
elif (condition): statement 3; statement 4
else: statement 5; statement 6
```

Multiple conditions in statements
It’s not that you can just write one condition within an if statement, it is still possible to evaluate multiple conditions like below:

```
num_1=10
num_2 = 20
num_3 =30
if (num_1==10 and num_2 == 20 and num_3 == 30):
    print("All conditions are true")
```
In this example, the if statement we’re evaluating using AND operator, this means if all the conditions are true then the statement inside will be implemented.

It's also possible to specify the OR operators too.
For example:

```
namefruit = "Apple"
if (namefruit == "Mango" or namefruit == "Apple" or namefruit == "Grapes"):
    print("One of the conditions is true")
```
In this example, out of the three conditions, only one condition is true, that's the rule of OR operator. If any one condition is true, then the statement available inside the block will be implemented.

Let's explore a real-time scenario to determine the number of days present in a month. You know that in a leap year the number of days will change. will see this in the programmatic way using if, elif, and else statements.

```
currentYear = int("Enter the year: ")
month = int("Enter the month: ")
if (currentYear % 4 == 0 and (currentYear % 100 != 0) or (currentYear % 400 == 0)):
    print("Leap Year")
    if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10 or month == 12):
        print("There are 31 days in this month")
    elif (month == 4 or month == 6 or month == 9 or month == 11):
        print("There are 30 days in this month")
    elif (month == 2):
        print("There are 29 days in this month")
    else:
        print("Invalid month")
elif ((currentYear % 4 != 0 and (currentYear % 100 != 0)) or (currentYear % 400 == 0)):
    if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10 or month == 12):
        print("There are 31 days in this month")
    elif (month == 4 or month == 6 or month == 9 or month == 11):
        print("There are 30 days in this month")
    elif (month == 2):
        print("There are 28 days in this month")
    else:
        print("Invalid month")
else:
    print("Invalid Year")
```
