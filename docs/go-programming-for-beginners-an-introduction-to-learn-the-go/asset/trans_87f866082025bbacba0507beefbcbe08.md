
# 位运算符

| 运算符 | 名称 | 示例 | 说明 |
| :--- | :--- | :--- | :--- |
| `^` | 按位逻辑异或 | `x ^ y` | 对操作数的每一位执行逻辑异或运算。 |
| `<<` | 左移 | `x << y` | 左操作数的位向左移动右操作数指定的次数。例如，`x << 3` 将 `x` 的位左移 3 次。 |
| `>>` | 右移 | `x >> y` | 左操作数的位向右移动右操作数指定的次数。例如，`y >> 5` 将 `y` 的位右移 5 次。 |

以下是位运算符的演示。动词 `%b` 和 `%X` 分别用于以二进制和十六进制格式打印值。

```go
/* Bitwise Operators Demo */
/* Package Declaration */
package main

/* Import Statement - import fmt package */
import (
	"fmt"
)

/* Mandatory main function */
func main() {
	/* Declare two integers */
	var x, y int = 23, 42

	/* Print values of x and y in decimal, binary and hex format */
	fmt.Printf("\nx (decimal) = %d, x (binary) = %b, x (hexadecimal) = %X", x, x, x)
	fmt.Printf("\ny (decimal) = %d, y (binary) = %b, y (hexadecimal) = %X", y, y, y)

	/* Print the result of bitwise operations */
	fmt.Printf("\n\nBitwise AND (&)\nx & y (decimal) = %d, x & y (binary) = %b, x & y (hexadecimal) = %X\n", x&y, x&y, x&y)
	fmt.Printf("\nBitwise OR (|)\nx | y (decimal) = %d, x | y (binary) = %b, x | y (hexadecimal) = %X\n", x|y, x|y, x|y)
	fmt.Printf("\nBitwise XOR (^)\nx ^ y (decimal) = %d, x ^ y (binary) = %b, x ^ y (hexadecimal) = %X\n", x^y, x^y, x^y)
	fmt.Printf("\nLeft Shift (<<)\nx << 1 (decimal) = %d, x << 1 (binary) = %b, x << 1 (hexadecimal) = %X\n", x<<1, x<<1, x<<1)
	fmt.Printf("\nRight Shift (>>)\ny >> 3 (decimal) = %d, y >> 3 (binary) = %b, y >> 3 (hexadecimal) = %X\n", y>>3, y>>3, y>>3)
}
```

**Output:**
![Output](Image00031.jpg)

# 9.5 赋值运算符

我们已经了解了由等号（`=`）表示的标准赋值运算符。Go 语言中还有更多运算符用于执行复合赋值操作。

| 运算符 | 说明 | 示例用法 | 等价于 |
| :--- | :--- | :--- | :--- |
| `+=` | 执行算术加法，然后将和赋值给左操作数。 | `x += y` | `x = x + y` |
| `-=` | 从左操作数中减去右操作数，并将差值赋值给左操作数。 | `x -= y` | `x = x - y` |
| `*=` | 相乘操作数并将积赋值给左操作数。 | `x *= y` | `x = x * y` |
| `/=` | 将左操作数除以右操作数，并将商赋值给左操作数。 | `x /= y` | `x = x / y` |
| `%=` | 将左操作数除以右操作数，并将余数赋值给左操作数。 | `x %= y` | `x = x % y` |
| `&=` | 执行按位逻辑与运算，将结果赋值给左操作数。 | `x &= y` | `x = x & y` |
| `\|=` | 执行按位逻辑或运算，将结果赋值给左操作数。 | `x \|= y` | `x = x \| y` |
| `^=` | 执行按位逻辑异或运算，将结果赋值给左操作数。 | `x ^= y` | `x = x ^ y` |
| `<<=` | 执行左移操作，将结果赋值给左操作数。 | `x <<= y` | `x = x << y` |
| `>>=` | 执行右移操作，将结果赋值给左操作数。 | `x >>= y` | `x = x >> y` |

让我们编写一个 Go 程序来演示不同赋值运算符的用法。

```go
/* Assignment Operators Demo */
/* Package Declaration */
package main

/* Import Statement - import fmt package */
import (
	"fmt"
)

/* Mandatory main function */
func main() {
	/* Declare two integers */
	var num1, num2 int = 35, 20

	fmt.Printf("\nnum1 = %d num2 = %d", num1, num2)

	/* Perform various compound assignment operations and print */
	num1 += num2
	fmt.Printf("\nnum1 += num2 = %d", num1)

	num1 -= num2
	fmt.Printf("\nnum1 -= num2 = %d", num1)

	num1 *= num2
	fmt.Printf("\nnum1 *= num2 = %d", num1)

	num1 /= num2
	fmt.Printf("\nnum1 /= num2 = %d", num1)

	num1 %= num2
	fmt.Printf("\nnum1 %%= num2 = %d", num1)

	num1 &= num2
	fmt.Printf("\nnum1 &= num2 = %d (decimal) / %%b (binary)", num1, num1)

	num1 |= num2
	fmt.Printf("\nnum1 \|= num2 = %d (decimal) / %%b (binary)", num1, num1)

	num1 ^= num2
	fmt.Printf("\nnum1 ^= num2 = %d (decimal) / %%b (binary)", num1, num1)

	num2 <<= 1
	fmt.Printf("\nnum2 <<= 1 = %d (decimal) / %%b (binary)", num2, num2)

	num2 >>= 3
	fmt.Printf("\nnum2 >>= 3 = %d (decimal) / %%b (binary)\n", num2, num2)
}
```

**Output:**
