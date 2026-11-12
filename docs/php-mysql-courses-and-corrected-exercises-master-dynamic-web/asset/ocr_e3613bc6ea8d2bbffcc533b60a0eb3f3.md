In the first call of the function **addition(5, 10)**, the two arguments are integers ($a = 5$ and $b = 10$). The function returns the sum of these two numbers, which is 15, and this value is then assigned to the variable $result1. Finally, the value of $result1 is displayed, producing 15 on the output.

In the second call of the function **addition(5, "10")**, the first argument is an integer ($a = 5$), but the second argument is a string ($b = "10"$). PHP performs an **automatic type conversion** on addition, converting the string "10" into an integer. Consequently, the function also returns 15 (the sum of 5 and 10), and this value is assigned to the variable $result2. Finally, the value of $result2 is displayed, also producing 15 on the output.

In summary, the result of both calls to the addition function is the same (15), even though the second call uses a string for the second argument. This is due to the automatic type conversion performed by PHP during the addition operation.

# Strict typing

Strict typing, introduced with PHP 7, makes it possible to explicitly specify the data types of parameters and function return values. This allows type inconsistencies to be detected as early as the development phase, which can help reduce errors.

To enable strict typing, you must declare the declaration: **declare(strict_types=1);** at the beginning of your PHP script: