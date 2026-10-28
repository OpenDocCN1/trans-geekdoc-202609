
## How to use the logical operators

The first table in figure 8-3 lists the three logical operators that you learned about in chapter 2. This table is followed by three examples that use these operators in a compound conditional expression. Since these expressions use just one of the logical operators, this type of expression is relatively easy to evaluate.

In the first example, the NOT operator reverses the Boolean value that's returned by the is_numeric function. As a result, this expression is TRUE when the value of the variable named $number is not a number. In the second example, the AND operator is used to return TRUE only when the age is 18 or higher and the score is 680 or higher.

In the third example, the OR operator is used to return TRUE if the state is either CA or NC. A common mistake when using the OR operator is to write an expression like this:

```
$state == 'CA' || 'NC'
```

In this case, the string 'NC' is converted to a Boolean TRUE value and the result of the comparison is always TRUE, which isn't what you want.

The second table in this figure shows the order of precedence for conditional expressions. For instance, this table shows that relational operations are done before equality and identity operations, and AND operations are done before OR operations. This table is followed by three examples that use these operators in complex conditional expressions. Since these expressions use two or more of the logical operators, these expressions are more difficult to evaluate.

In the first example, the AND and OR operators are used in the conditional expression. Because the AND operator is evaluated first, this expression returns TRUE if the age is 18 or more and the score is 680 or more regardless of the state. This expression also returns TRUE if the state is NC regardless of the age and score.

In the second example, the AND, OR, and NOT operators are used in one expression. This expression returns TRUE if $old_customer is FALSE. It also returns TRUE if the loan amount is greater than or equal to 10000 and the score is less than the minimum score plus 200. Note that this expression uses an arithmetic operator, which is evaluated before the relational operators.

In the third example, parentheses change the order of precedence of the operators that are in the fifth example. This time, the OR operation is coded inside a set of parentheses. As a result, this expression returns TRUE if old_customer is FALSE and the score is less than the minimum score plus 200. It also returns TRUE if the loan amount is greater than or equal to 10000 and the score is less than the minimum score plus 200.

As these examples illustrate, complex conditional expressions are hard to code. That's why you should use parentheses to clarify the order of evaluation whenever you are in doubt. But even then, you need to carefully test these expressions with all of the possible combinations of data to make sure they work correctly.

### The logical operators

| Operator | Name | Description |
|---|---|---|
| `!` | NOT | Returns the opposite Boolean value of its expression. |
| `&&` | AND | Returns TRUE only when the expressions on both sides are TRUE. |
| `\|\|` | OR | Returns TRUE when the expression on either side or both sides is TRUE. |

### The logical operators in compound conditional expressions

**The NOT operator**

```
!is_numeric($number)
```

**The AND operator**

```
$age >= 18 && $score >= 680
```

**The OR operator**

```
$state == 'CA' || $state == 'NC'
```

### The order of precedence for operators in conditional expressions

| Order | Operators | Description |
|---|---|---|
| 1 | `!` | The NOT operator |
| 2 | `<`, `<=`, `>`, `>=`, `<>` | Relational operators |
| 3 | `==`, `!=`, `===`, `!==` | Equality and identity operators |
| 4 | `&&` | The AND operator |
| 5 | `\|\|` | The OR operator |

### The logical operators in complex conditional expressions

**AND and OR operators**

```
$age >= 18 && $score >= 680 || $state == 'NC'
```

**AND, OR, and NOT operators**

```
!$old_customer || $loan_amount >= 10000 && $score < $min_score + 200
```

### How parentheses can change the evaluation

```
(!$old_customer || $loan_amount >= 10000) && $score < $min_score + 200
```

### Description

- Parentheses have the highest order of precedence so the operations within parentheses are done first, working from the innermost sets of parentheses to the outermost sets.
- To clarify the way an expression is evaluated, you should use parentheses.
- You can use arithmetic expressions within a conditional expression. In the order of precedence, the arithmetic operators come between the NOT operator and the relational operators.

## An if clause with one statement and no braces

```
if (!isset($rate)) $rate = 0.075;
```

## An if clause with one statement and braces

```
if ($qualified) { // This expression is equivalent to $qualified == true.
    echo 'You qualify for enrollment.';
}
```

## If and else clauses with one statement each and no braces

```
if ($age >= 18)
    echo 'You may vote.';
else
    echo 'You may not vote.';
```

## Why you should always use braces with else clauses

```
if ($age >= 18)
    echo 'You may vote.';
else
    echo 'You may not vote.';
$may_vote = false;    // This statement isn't a part of the else clause.
```

## Braces make your code easier to modify or enhance

```
if ($score >= 680) {
    echo 'Your loan is approved.';
} else {
    echo 'Your loan is not approved.';
}
```

## A nested if statement to determine if a year is a leap year

```
$is_leap_year = false;
if ($year % 4 == 0) {
    if ($year % 100 == 0) {
        if ($year % 400 == 0) {
            $is_leap_year = true;      // divisible by 4, 100, and 400
        } else {
            $is_leap_year = false;     // divisible by 4 and 100, but not 400
        }
    } else {
        $is_leap_year = true;          // divisible by 4, but not 100
    }
} else {
    $is_leap_year = false;             // not divisible by 4
}
```

### Description

- If you only have one statement after an if statement or an else clause, you don’t have to put braces around that statement.
- You can nest an if statement within the if, else if, or else clause of another if statement. This nesting can continue many layers deep.

## How to code if statements with else if clauses

Figure 8-5 presents four examples of if statements that use else if clauses. In the first example, for instance, if the age is less than 18, the if clause displays a message. However, if the age is 18 or more, PHP evaluates the else if clause. Then, if the score is less than 680, the else if clause displays a message.

The second example shows that the else if clause can also be coded with the elseif keyword (no space between the else and if keywords). In this book, we typically include a space between the keywords, but you can use either style, though you should try to be consistent with the style that you choose.

The third example shows how to use else if clauses to validate the value in the variable named $rate. Before the if statement starts, a Boolean variable named $rate_is_valid is set to FALSE. Then, the if statement uses a series of tests to determine the validity of the $rate variable, starting with the worst case first (is not a number). If any of the tests fails, an appropriate message is displayed. But if the variable passes all of the tests, the $rate_is_valid variable is set to TRUE.

The fourth example also shows the use of multiple else if clauses. This code tests the value of the variable named $average in order to set the value of the variable named $grade. Note that these values must be tested from the high end of the range to the low. If, for example, you code the first test like this

```
$average >= 69.5
```

it won’t work for the A and B ranges. To fix this problem, you can code the first test like this

```
$average >= 69.5 && $average < 79.5
```

However, that would mean extra code. Also, this would make the code harder to read and maintain. In general, then, it’s best to test for a range of values in sequence.

Incidentally, these examples illustrate a common coding style, where the else if or else keywords are on the same line as the closing brace for the previous clause. This helps keep the code compact yet readable.

If you work with PHP code, you may see other styles. For example, some programmers prefer to code each brace on its own line. This approach also works and is easy to read, but it takes more vertical space.
