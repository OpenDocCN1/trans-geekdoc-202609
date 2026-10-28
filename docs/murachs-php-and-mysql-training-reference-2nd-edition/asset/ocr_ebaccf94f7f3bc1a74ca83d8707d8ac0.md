# How to code if statements

An *if statement* lets you control the execution of statements based on the results of one or more conditional expressions. Figure 2-15 shows that an if statement can include three types of clauses. This statement must begin with an *if clause*. Then, it can have one or more *else if clauses*, but it doesn’t have to have any. Last, it can have an *else clause*, but that clause is also optional.

To code the if clause, you code the *if* keyword followed by a conditional expression in parentheses and a block of one or more statements inside braces. If the conditional expression is TRUE, this block of code is executed and any remaining clauses in the if statement are skipped over. If the conditional expression is FALSE, the if statement continues with the next clause.

To code an else if clause, you code the *else if* keywords followed by a conditional expression in parentheses and a block of one or more statements inside braces. If the conditional expression is TRUE, its block of code is executed and any remaining clauses in the if statement are skipped over. This continues until one of the else if expressions is TRUE or they all are FALSE.

To code an else clause, you code the *else* keyword followed by a block of one or more statements inside braces. This code is only executed if all the conditional expressions in the if and else if clauses are FALSE.

The first example in this figure shows an if statement with no other clauses. If the price is less than or equal to zero, an appropriate message is stored in the `$message` variable.

The second example shows an if statement with an else clause. If the `$first_name` variable is empty, the statement in the if clause executes. Otherwise, the statement in the else clause executes.

The third example shows an if statement with two else if clauses and an else clause. If the `$investment` variable is empty, the if clause executes. If the `$investment` variable is *not* a valid number, the first else if clause executes. If the `$investment` variable is less than or equal to zero, the second else if clause executes. Otherwise, the else clause executes.

The fourth example shows an if statement with a compound conditional expression that tests whether the `$investment` variable is empty, is not a number, or is less than or equal to zero. If any of these conditions are TRUE, this code executes the statement within the if clause. If all three expressions are FALSE, this code doesn’t execute any statements.

The last example shows how to nest one if statement within another. Here, the second if statement is nested within the else clause of the first if statement. When these *nested if statements* are executed, an error message is displayed if the `$months` variable is empty, is not a number, or is less than or equal to zero. This ends the if statement and nothing else happens. But if the `$months` variable is a number that’s greater than zero, the else clause calculates the number of years represented by the `$months` variable. Then, the if statement that’s nested in the else clause checks if the years are greater than 1 and sets the `$message` variable to an appropriate message.