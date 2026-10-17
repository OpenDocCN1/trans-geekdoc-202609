
The following samples show how this logical construct appears with and without blocks:

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `if (condition)`<br>`{`<br>`    code_if_true;`<br>`}`<br>`else`<br>`{`<br>`    code_if_false;`<br>`}` | `if (!condition)`<br>`    goto false_block;`<br>`code_if_true;`<br>`goto skip_block;`<br>`false_block:`<br>`code_if_false;`<br>`skip_block:` |

Note that the code uses two different labels in its `goto` statements. The label `false_block` is used to skip over the `if` block if the condition is false, while the label `skip_block` is used to jump past the `else` block after executing the `if` block. Just like before, invert the conditional statement when rewriting code without blocks.

Replacing the pseudocode with actual code yields the following with and without code blocks:

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `if (x)`<br>`{`<br>`    x++;`<br>`}`<br>`else`<br>`{`<br>`    x--;`<br>`}` | `if (!x)`<br>`    goto false_block;`<br>`x++;`<br>`goto skip_block;`<br>`false_block:`<br>`x--;`<br>`skip_block:` |

As before, removing the blocks makes it easier to convert the high-level code into assembly code.

| CODE | X86 ASSEMBLY |
| --- | --- |
| `if (!x)`<br>`    goto false_block;`<br>`x++;`<br>`goto skip_block;`<br>`false_block:`<br>`x--;`<br>`skip_block:` | `cmp dword [x], 0`<br>`je false_block`<br>`inc dword [x]`<br>`jmp skip_block`<br>`false_block:`<br>`dec dword [x]`<br>`skip_block:` |

#### `if (…) { … } else if { … } else { … }`

`if` statements can be made more complex and evaluate multiple different conditions. The following demonstrates an `if` statement with `else if` and `else` with and without blocks. But the process still stays the same. Invert the condition, and add `goto`s.

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `if (condition_1)`<br>`{`<br>`    code_if_1;`<br>`}`<br>`else if (condition_2)`<br>`{`<br>`    code_if_2;`<br>`}`<br>`else`<br>`{`<br>`    code_if_false;`<br>`}` | `if (!condition_1)`<br>`    goto test_2;`<br>`code_if_1;`<br>`goto skip_block;`<br>`test_2:`<br>`if (!condition_2)`<br>`    goto false_block;`<br>`code_if_2;`<br>`goto skip_block;`<br>`false_block:`<br>`code_if_false;`<br>`skip_block:` |

Note that, once again, converting to a blockless version requires flipping the conditions. The strictly less than statements become greater than or equal to 1. The following example shows how this code is then easily translated to assembly:

| CODE | X86 ASSEMBLY |
| --- | --- |
| `if (score<=70)`<br>`    goto test_2;`<br>`grade='a';`<br>`goto skip_block;`<br>`test_2:`<br>`if (score<=50)`<br>`    goto false_block;` | `cmp dword [score], 70`<br>`jle test_2`<br>`mov byte [grade], 'a'`<br>`jmp skip_block`<br>`test_2:`<br>`cmp dword [score], 50`<br>`jle false_block` |
| `grade='b';`<br>`goto skip_block;`<br>`false_block:`<br>`grade='c';`<br>`skip_block:` | `mov byte [grade], 'b'`<br>`jmp skip_block`<br>`false_block:`<br>`mov byte [grade], 'c'`<br>`skip_block:` |

### `do { ... } while (...);`

Higher-level programming languages have a number of different loop structures, each of which works slightly differently. A `do…while` loop is guaranteed to perform at least one iteration before evaluating the condition that would terminate the loop. The following is an example of a `do…while` loop with blocks:

```
do
{
    code;
}
while (condition);
```

- [与 `if` 语句不同，`do…while` 循环在循环的末尾评估其条件，因此要继续循环需要向后跳转。如前所述，此代码需要重写为不使用代码块的形式。下面展示了使用 `goto` 语句而非代码块的相同 `do…while` 循环：]

```
loop:
 
code;
 
if (condition)
    goto loop;
```

- [与 `if` 语句不同，`do..while` 循环不会对其被测试的条件进行取反。这是因为向后跳转仅在条件为真且需要再次通过循环时执行。]

- [现在，请查看使用真实条件和逻辑的代码版本。]

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `do`<br>`{`<br>`    y*=x;`<br>`    x--;`<br>`}`<br>`while (x);` | `loop:`<br>`y*=x;`<br>`x--;`<br>`if (x)`<br>`    goto loop;` |

- [将此代码转换为不使用代码块相对简单，因为指令流基本保持不变。主要区别在于将 `while` 语句替换为 `if` 和 `goto`。]

- [与前面的示例不同，将此转换为汇编代码的复杂性主要取决于示例代码的复杂性，而非分支结构。]

| CODE | X86 ASSEMBLY |
| --- | --- |
| `loop:`<br>`y*=x;`<br>`x--;`<br>`if (x)`<br>`    goto loop;` | `loop:`<br>`mov eax, [y]`<br>`mul dword [x]`<br>`mov [y], eax`<br>`sub dword [x], 1`<br>`cmp dword [x], 0`<br>`jne loop` |

- [`do…while` 循环保证在条件被评估之前至少执行一次循环体。`while` 循环立即评估条件，因此循环体可能根本不执行。下面的表格展示了带代码块和不带代码块的 `while` 循环。`while` 循环可以分解为 `if` 语句，因此遵循常规的 `if` 语句转换模式。]

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `while (condition)`<br>`{`<br>`    code;`<br>`}` | `loop:`<br>`if (!condition)`<br>`    goto done;`<br>`code;`<br>`goto loop;`<br>`done:` |

- [由于条件在循环开始时评估，它的逻辑与 `if` 语句相同（需要取反）。下面的表格展示了从伪代码到实际代码的转换示例：]

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `while (tired)`<br>`{`<br>`    sleep();`<br>`}` | `loop:`<br>`if (!tired)`<br>`    goto done;`<br>`sleep();`<br>`goto loop;`<br>`done:` |

- [代码去除代码块后，可转换为 x86 汇编如下：]

| CODE | X86 ASSEMBLY |
| --- | --- |
| `loop:`<br>`if (!tired)`<br>`    goto done;`<br>`sleep();`<br>`goto loop;`<br>`done:` | `loop:`<br>`cmp dword [tired], 0`<br>`je done`<br>`call sleep`<br>`jmp loop`<br>`done:` |

- [`for` 循环的运行方式不同于 `while` 或 `do…while` 循环。它包含三个表达式：初始化循环计数器、定义循环终止条件、以及在每次迭代中更新计数器的表达式。]

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `for (expr_1; expr_2; expr_3)`<br>`{`<br>`    code;`<br>`}` | ` expr_1;`<br>` loop:`<br>` if (!expr_2)`<br>`    goto done;`<br>` code;`<br>` expr_3;`<br>` goto loop;`<br>` done:` |

- [在去除代码块后，`for` 循环的三个表达式会被拆分：第一个表达式在循环开始前执行一次，第二个表达式开始循环，第三个表达式在每次迭代结束时执行以更新计数器。]

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `for (i=0; i<100; i++)`<br>`{`<br>`    sum+=i;`<br>`}` | ` i=0;`<br>` loop:`<br>` if (i>=100)`<br>`    goto done;`<br>` sum+=i;`<br>` i++;`<br>` goto loop;`<br>` done:` |

- [与 `while` 或 `if` 语句一样，`for` 循环在条件评估时会取反条件，因为条件在循环开始时而非结束时评估。]

| CODE | X86 ASSEMBLY |
| --- | --- |
| ` i=0;`<br>` loop:`<br>` if (i>=100)`<br>`    goto done;`<br>` sum+=i;`<br>` i++;`<br>` goto loop;`<br>` done:` | `mov dword [i], 0`<br>`loop:`<br>`cmp dword [i], 100`<br>`jge done`<br>`mov eax,[i]`<br>`add [sum],eax`<br>`inc dword [i]`<br>`jmp loop`<br>`done:` |

- [`switch` 语句是某些编程语言中用于根据变量值选择执行不同操作的逻辑结构。下面的示例根据变量 `op` 的值打印对应的字符：]

```
 typedef enum {ADD, SUB, MUL, DIV, MOD} op_t;
 
switch (op) {
    case ADD:
        c='+'; break;
    case SUB:
        c='-'; break;
    case MUL:
        c='*'; break;
    case DIV:
        c='/'; break;
    case MOD:
        c='%'; break;
    default:
        c='?'; break;
}
```

- [任何 `switch` 语句都可以用一系列 `if` 和 `else-if` 语句表示，但这样会导致代码复杂且执行效率低。例如，若要匹配最后一个案例，需要依次执行所有前面的比较。]

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `while (condition)`<br>`{`<br>`    code;`<br>`}` | `loop:`<br>`if (!condition)`<br>`    goto done;`<br>`code;`<br>`goto loop;`<br>`done:` |

- [下面的表格展示了 `switch` 语句的 `if`/`else-if` 等价形式：]

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `while (tired)`<br>`{`<br>`    sleep();`<br>`}` | `loop:`<br>`if (!tired)`<br>`    goto done;`<br>`sleep();`<br>`goto loop;`<br>`done:` |

- [下面的表格展示了 `for` 循环的 `if`/`else-if` 等价形式：]

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `for (expr_1; expr_2; expr_3)`<br>`{`<br>`    code;`<br>`}` | ` expr_1;`<br>` loop:`<br>` if (!expr_2)`<br>`    goto done;`<br>` code;`<br>` expr_3;`<br>` goto loop;`<br>` done:` |

- [下面的表格展示了 `for` 循环的 x86 汇编实现：]

| CODE | X86 ASSEMBLY |
| --- | --- |
| ` i=0;`<br>` loop:`<br>` if (i>=100)`<br>`    goto done;`<br>` sum+=i;`<br>` i++;`<br>` goto loop;`<br>` done:` | `mov dword [i], 0`<br>`loop:`<br>`cmp dword [i], 100`<br>`jge done`<br>`mov eax,[i]`<br>`add [sum],eax`<br>`inc dword [i]`<br>`jmp loop`<br>`done:` |

- [`switch` 语句通过枚举类型 `op_t` 根据变量 `op` 的值选择执行不同操作。下面的 `switch` 语句根据 `op` 的值打印对应的字符：]
