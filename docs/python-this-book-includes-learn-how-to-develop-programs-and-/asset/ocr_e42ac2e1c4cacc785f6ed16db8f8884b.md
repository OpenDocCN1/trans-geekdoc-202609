AND operator, this means if all the conditions are true only when the\statements within an if block will be implemented.
It's also possible to specify the OR operators too.
For example:
namefruit = "Apple"
if (namefruit == "Mango" or namefruit == "Apple" or namefruit =
"Grapes\):
In this example, out of the three conditions, only one condition is true,
that's the rule of OR operator. If any one condition is true, then the condition
true and the statement available inside the block will be implemented.
Let's explore a real-time scenario to determine the number of days present in a month. You know that in a leap year the number of days will change.
will see this in the programmatic way using if, elif, and else statements.

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
elif ((currentYear % 4 != 0 and (currentYear % 100 != 0) or (currentYear % 400 == 0)):
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