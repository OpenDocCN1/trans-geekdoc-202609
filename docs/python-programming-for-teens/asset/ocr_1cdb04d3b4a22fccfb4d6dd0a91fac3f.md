# The Two-Way if Statement

Two-way decisions, like forks in the road, are common. You go one way or the other, depending on the condition you examine at the choice point. The form for a two-way if statement to make this type of choice is

```
if BooleanExpression:
    ConsequentStatements
else:
    AlternativeStatements
```

Once again, the indentation of the nested statements reflects the logic of this control structure. If the Boolean expression is True, run the consequent statements and then skip to the end of the entire if-else statement. Otherwise, skip the consequent statements and run the alternative statements following the keyword else. Figure 3.3 shows the flow of control in this type of selection statement.

![](bbox=[0.06, 0.44, 0.78, 0.68])

Figure 3.3
The flow of control in a two-way if statement.

Here is an example of how you can use an if-else statement to accept or reject a user’s input number:

```
>>> import math
>>> number = input("Enter a positive number: ")
>>> if number > 0:
    print("The square root is", math.sqrt(number))
else:
    print("Error: the number must be greater than 0")
```