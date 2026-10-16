
## `switch` 语句与跳转表

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

下面的代码展示了使用 `if` 和 `else-if` 语句实现的等价 `switch`：

```
if (op==ADD)
    c='+';
else if (op==SUB)
    c='-';
else if (op==MUL)
    c='*';
else if (op==DIV)
    c='/';
else if (op==MOD)
    c='%';
else
    c='?';
```

为了避免在执行大量 `if`/`else-if` 检查时的低效，编译器可以构建**跳转表**（jump table）。跳转表是一种汇编数据结构，存储 `switch` 语句各分支的目标地址，使得根据 case 编号直接索引到对应代码块，实现直接跳转。

![Figure 7.1: Example jump table](img/c07f001.png)

**Figure 7.1**: Example jump table

下面的代码展示了使用跳转表的汇编实现：

```
.section data
table:
dd target_0
dd target_1
dd target_2
dd target_3
dd target_4

.section text
mov eax, [op]
cmp eax, 5
jge default
jmp [table+eax*4]

target_0:
mov byte [c], '+'
jmp done

target_1:
mov byte [c], '-'
jmp done

target_2:
mov byte [c], '*'
jmp done

target_3:
mov byte [c], '/'
jmp done

target_4:
mov byte [c], '%'
jmp done

default:
mov byte [c], '?'
jmp done

done:
```

It begins with the jump table, which contains the addresses of the various code blocks in memory. Each of these code blocks, labeled as `target_x`, moves the appropriate character into `byte [c]` and then jumps to the `done` label.

In between the table and the target code blocks is the code that actually implements the `switch` statement under the `.section text` heading. This code begins by moving `op` into `eax`. It then checks if `op` is greater than or equal to 5. If so, it jumps to the `default` case.

If the value of `op` is less than 5, it maps to one of the targets. By using it as a lookup into the jump table, the processor can retrieve the address of the corresponding code block and jump to that location to execute the code.

In this case, using the jump table, the execution time is the same regardless of which case it is. The last case doesn't take any more instructions or comparisons than the first.

### Missing Cases

A jump table assumes that the cases cover a continuous range of values. For example, in the following code sample, a `switch` statement has the cases 1, 2, 4, and 5. In this scenario, the missing 3 can be a problem. Something needs to go in the third spot in the jump table.

```
switch (x) {
    case 0:
        …
    case 1:
        …
    case 2:
        …
    case 4:
        …
    default:
        …
}
```

Missing values in a jump table can be filled with the `default` address or `done` if there is no `default`, as shown next. This will cause the processor to jump to the proper location when `op` equals 3, and it attempts to jump to the corresponding location in the jump table.

**JUMP TABLE**

|  |
| --- |
| `target_0` |
| `target_1` |
| `target_2` |
| `default` |
| `target_4` |

### Nonzero Bases

A jump table is designed to have a set of cases that start at 0. However, a `switch` statement may have nonzero case values, as shown in the following code sample:

```
switch (x) {
    case 'a':
        …
    case 'b':
        …
    case 'c':
        …
    case 'd':
        …
}
```

In this case, it's necessary to find a way to zero the cases. With ASCII, it's necessary to find the lowest case in the jump table that, for this example, has a value of `a`, or 97. When implementing a jump table for this `switch` statement, the code can use an offset, accessing values as `table[x-97]`. In the following jump table, `target_a` will point to case `a` of the `switch` statement.

**JUMP TABLE**

|  |
| --- |
| `target_a` |
| `target_b` |
| `target_c` |
| `target_d` |

### Impractical Jump Tables

A compiler will use these tricks to improve code efficiency, and you can too when writing code by hand. However, sometimes a jump table just won't work. For example, consider the following code:

```
switch (x) {
    case 1:
        printf("this is the beginning."); break;
    case 1000:
        printf("this is the end."); break;
}
```

A jump table for this `switch` statement would need to have 1,000 entries and 998 of them would point to the `done` label. In this case, an `if/else` statement is the more efficient option.

That's not the only case where it's impractical; a larger jump table with hundreds of cases, or a table that uses an index that can't easily be zeroed or has too many gaps in the table, can be impractical. But as you both write and dissect assembly code, it's important to be able to understand these structures and how they're used.

## Continue

Some higher-level languages include the `continue` keyword. `continue` is used inside a loop and instructs the processor to jump to the next iteration of the loop, skipping any instructions that follow.

For example, in the following code sample, the second section labeled `code` would be unreachable. Each time the `continue` statement is evaluated, the processor jumps directly to the `while` statement.

```
do
{
    code;
    continue;
    code;
}
while (condition);
```

A loop with a `continue` statement looks similar to a normal loop of that type when written without code blocks. As shown next, a `continue` can be implemented by using a `goto` that jumps to a label located right before the loop condition.

```
loop:
code;
goto check_condition;
code;

check_condition:
if (condition)
    goto loop;
```

The following examples show an example of a loop with a `continue` statement using actual code:

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `do`<br>`{`<br>`    x--;`<br>`    continue;`<br>`    x++;`<br>`}`<br>`while (x);` | `loop:`<br>`x--;`<br>`goto check_condition;`<br>`x++;`<br>`check_condition:`<br>`if (x)`<br>`    goto loop;` |

In this code, the instruction `x++;` will never execute because the `continue` always causes it to be skipped. Typically, a `continue` will be located inside of an `if` statement because, otherwise, the code following it is pointless. This contrived example is designed to demonstrate how `continue` works without the complexity of `if` statements nested within a loop.

Once the code has been converted to remove code blocks, it can be translated to assembly. As before, a `goto` can be implemented using a nonconditional jump.

| CODE | X86 ASSEMBLY |
| --- | --- |
| `loop:`<br>`x--;`<br>`goto check_condition;`<br>`x++;`<br>`check_condition:`<br>`if (x)`<br>`    goto loop;` | `loop:`<br>`sub dword [x], 1`<br>`jmp check_condition`<br>`add dword [x], 1`<br>`check_condition:`<br>`cmp dword [x], 0`<br>`jne loop` |

## break

The `break` keyword also exists in some programming languages, and it instructs the processor to exit the current loop. As with `continue`, the second chunk of code in the following example will never execute, as the `break` would typically be inside of a conditional statement, but this is an example simply to demonstrate the `break` mechanism.

```
do
{
    code;
    break;
    code;
}
while (condition);
```

The following example demonstrates how this code would be implemented without code blocks. The `break` keyword is also replaced with a `goto`, but this one jumps to a point outside of the loop rather than before the conditional.

```
loop:
code;
goto break;
code;

if (condition)
    goto loop;

break:
```

In the following example, the `break` statement would terminate the loop after the operation `x--` has been evaluated once. In this case, the `x++` statement and the loop conditional will never be executed, but again this is sample code. It shows how you'd easily put the `break` into a conditional.

| WITH BLOCKS | WITHOUT BLOCKS |
| --- | --- |
| `do`<br>`{`<br>`    x--;`<br>`    break;`<br>`    x++;`<br>`}` | |
