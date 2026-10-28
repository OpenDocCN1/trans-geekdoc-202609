
## An if statement with one else if clause

```
if ($age < 18) {
    echo "You're too young for a loan.";
} else if ($score < 680) {
    echo "Your credit score is too low for a loan.";
}
```

## An if statement with an else if and an else clause

```
if ($age < 18) {
    echo "You're too young for a loan.";
} elseif ($score < 680) {
    echo "Your credit score is too low for a loan.";
} else {
    echo "You're approved for your loan.";
}
```

## An if statement with two else if clauses and an else clause

```
$rate_is_valid = false;
if (!is_numeric($rate)) {
    echo 'Rate is not a number.';
} else if ($rate < 0) {
    echo 'Rate cannot be less than zero.';
} else if ($rate > 0.2) {
    echo 'Rate cannot be greater than 20%.';
} else {
    $rate_is_valid = true;
}
```

## An if statement to determine a student's letter grade

```
if ($average >= 89.5) {
    $grade = 'A';
} else if ($average >= 79.5) {
    $grade = 'B';
} else if ($average >= 69.5) {
    $grade = 'C';
} else if ($average >= 64.5) {
    $grade = 'D';
} else {
    $grade = 'F';
}
```

## Description

- When coding an else if clause, you can code the else and if keywords (with a space), or you can use the elseif keyword (no space).

## How to use the conditional operator

A ternary operator has three operands. In contrast, a unary operator such as ++ has one operand while a binary operator such as * has two operands. The conditional operator is PHP’s only ternary operator.

Since the conditional operator has three operands, it needs two symbols to separate them. In this case, the question mark and the colon are used as the operand separators. This is shown by the syntax in figure 8-6.

The first example in this figure shows how to use the conditional operator to set a variable to one of two values based on a comparison. If the age is 18 or more, the message is set to “Can vote”. Otherwise, the message is set to “Cannot vote”.

The second example shows how to use a mathematical expression in one of the operands. If $hours is over 40, $overtime contains 1.5 times the pay rate for the number of hours over 40. Otherwise, it is set to 0.

The third example shows how to select between a singular or plural ending for use in a message to the user. If $error_count is 1, the ending is empty. Otherwise, “s” is used for the ending.

The fourth example shows how to add one to a value or set it back to 1, depending on whether the value is at its maximum. For example, if $max_value is 10 and $value is 6, the test is FALSE and 1 is added to $value. However, when $value reaches 10, it is set to 1 instead.

If you need to perform this kind of rollover with a variable, but the starting value is 0 instead of 1, you don’t have to use the conditional operator. Instead, you can use the % operator. For example, in the statement

```
$value = ($value + 1) % ($max_value + 1);
```

If $max_value is 9, $value ranges from 0 to 9 and then back to 0.

The fifth example shows how to combine the conditional operator with the return keyword so the result is returned by a function. Here, if $number is greater than $highest, $highest is returned. Otherwise, $number is returned.

The last example shows how to keep a value within a fixed range. It uses a nested conditional operator to do this. If $value is greater than $max, $value is set to $max. If $value is not greater than $max, the second conditional operator is evaluated. Here, if $value is less than $min, $value is set to $min. If $value is not less than $min, $value is set to $value, leaving it unchanged.

The last two examples rewrite the first and sixth examples so they use if statements instead of the conditional operator. These statements show that if statements are easier to read than statements that use the conditional operator. As a result, if you want your code to be as easy to read as possible, you should avoid the conditional operator.

Nevertheless, many programmers like to use the conditional operator because it takes fewer lines of code. As a result, even if you don’t use the conditional operator in your code, you still need to understand how it works, so you can understand code that has been written by other programmers.

### Syntax of the conditional operator

```
(conditional_expression) ? value_if_true : value_if_false
```

### Examples of using the conditional operator

#### Set a string based on a comparison

```
$message = ($age >= 18) ? 'Can vote' : 'Cannot vote';
```

#### Calculate overtime pay

```
$overtime = ($hours > 40) ? ($hours - 40) * $rate * 1.5 : 0;
```

#### Select a singular or plural ending based on a value

```
$ending = ($error_count == 1) ? '' : 's';
$message = 'Found ' . $error_count . ' error' . $ending . '.';
```

#### Set a value to 1 if it’s at a maximum value when adding 1

```
$value = ($value >= $max_value) ? 1 : $value + 1;
```

#### Return one of two values based on a comparison

```
return ($number > $highest) ? $highest : $number;
```

#### Bound a value within a fixed range

```
$value = ($value > $max) ? $max : (($value < $min) ? $min : $value);
```

### The first example rewritten with an if statement

```
if ($age >= 18) {
    $message = 'Can vote';
} else {
    $message = 'Cannot vote';
}
```

### The last example rewritten with an if statement

```
if ($value > $max) {
    $value = $max;
} else if ($value < $min) {
    $value = $min;
}
```

### Description

- A ternary operator has three operands. The conditional operator is the only ternary operator available from PHP. This operator provides a compact way to code an if statement.
- The conditional operator begins by evaluating the conditional expression. Then, if the conditional expression is TRUE, the value that results from the middle expression is returned. Otherwise, the value that results from the last expression is returned.

## A switch statement with a default case

```
switch ($letter_grade) {
    case 'A':
        $message = 'well above average';
        break;
    case 'B':
        $message = 'above average';
        break;
    case 'C':
        $message = 'average';
        break;
    case 'D':
        $message = 'below average';
        break;
    case 'F':
        $message = 'failing';
        break;
    default:
        $message = 'invalid grade';
        break;
}
```

## A switch statement with fall through

```
switch ($letter_grade) {
    case 'A':
    case 'B':
        $message = 'Scholarship approved.';
        break;
    case 'C':
        $message = 'Application requires review.';
        break;
    case 'D':
    case 'F':
        $message = 'Scholarship not approved.';
        break;
}
```

## Description

- The *switch statement* starts by evaluating the *switch expression* in the parentheses.
- After evaluating the expression, the switch statement transfers control to the *case label* that has the value that matches the value of the expression. Then, it executes the statements for that *case*. It stops executing when it reaches a break statement or the end of the switch statement.
- The default case is optional and may be omitted. If included, you can only have one default case. It is usually the last case in the switch statement, but it can be anywhere.
- The values in the case label may be literal values or they may be expressions.
- If a case doesn’t contain a break statement, execution “falls through” to the next label.
- You can nest if statements or other switch statements within the cases of a switch statement.

## A switch statement in the controller for the Product Manager application

```php
$action = filter_input(INPUT_POST, 'action');
if ($action == NULL) {
    $action = filter_input(INPUT_GET, 'action');
    if ($action == NULL) {
        $action = 'list_products';
    }
}

switch ($action) {
    case 'list_products':
        $category_id = filter_input(INPUT_GET, 'category_id',
            FILTER_VALIDATE_INT);
        if ($category_id == NULL || $category_id == FALSE) {
            $category_id = 1;
        }
        $category_name = get_category_name($category_id);
        $categories = get_categories();
        $products = get_products_by_category($category_id);
        include('product_list.php');
        break;
    case 'delete_product':
        $product_id = filter_input(INPUT_POST, 'product_id',
            FILTER_VALIDATE_INT);
        $category_id = filter_input(INPUT_POST, 'category_id',
            FILTER_VALIDATE_INT);
        if ($category_id == NULL || $category_id == FALSE ||
            $product_id == NULL || $product_id == FALSE) {
            $error = "Missing or incorrect product id or category id.";
            include('../errors/error.php');
        } else {
            delete_product($product_id);
            header("Location: .?category_id=$category_id");
        }
        break;
    case 'show_add_form':
        $categories = get_categories();
        include('product_add.php');
        break;
    case 'add_product':
        $category_id = filter_input(INPUT_POST, 'category_id',
            FILTER_VALIDATE_INT);
        $code = filter_input(INPUT_POST, 'code');
        $name = filter_input(INPUT_POST, 'name');
        $price = filter_input(INPUT_POST, 'price');
        if ($category_id == NULL || $category_id == FALSE || $code == NULL ||
            $name == NULL || $price == NULL || $price == FALSE) {
            $error = "Invalid product data. Check all fields and try again.";
            include('../errors/error.php');
        } else {
            add_product($category_id, $code, $name, $price);
            header("Location: .?category_id=$category_id");
        }
        break;
}
```
