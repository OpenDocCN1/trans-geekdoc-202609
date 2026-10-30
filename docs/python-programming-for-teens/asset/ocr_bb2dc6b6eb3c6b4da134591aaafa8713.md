Table 3.2 The Truth Table for Logical Conjunction and Logical Disjunction

| A | B | A and B | A or B |
|---|---|---|---|
| True | True | True | True |
| True | False | False | True |
| False | True | False | True |
| False | False | False | False |

You probably won’t use logical operations very often. But if you need help with them, you can always review these tables for their evaluation rules and then try your expressions in the shell.

# MAKING CHOICES: SELECTION STATEMENTS

After you determine how to ask a yes/no question about a condition, you must decide what to do with the answer. Sometimes you take action if the answer is “yes” but do nothing if it is “no.” For example, if the remainder of an integer division is not 0, you would output the remainder; otherwise, the output of the quotient, which happened earlier, would suffice.

Other times, you perform one action if the answer to your question is “yes” but another action if the answer is “no.” For example, if a password is recognized, you can perform the requested service; otherwise, you output an error message to the user.

Still other times, there may be many different options available, but only one of them is input. You must compare the input to each possible option until a match is found, whereupon you perform the associated action. Command menus call for this type of multiway decision.

In this section, you explore Python’s different types of selection statements for making one-way, two-way, and multiway decisions.

# The One-Way if Statement

You use the one-way if statement to make a one-way decision. Its form is

```
if BooleanExpression:
    Statements
```