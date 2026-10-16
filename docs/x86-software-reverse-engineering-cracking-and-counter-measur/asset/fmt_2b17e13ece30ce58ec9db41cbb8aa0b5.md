
It begins with the jump table, which contains the addresses of the various code blocks in memory. Each of these code blocks, labeled as `*target_x*` , moves the appropriate character into `byte` [c] and then jumps to the `*done*` label.

In between the table and the target code blocks is the code that actually implements the `switch` statement under the `.section text` heading. This code begins by moving `*op*` into `eax` . It then checks if `*op*` is greater than or equal to 5. If so, it jumps to the `*default*` case.

If the value of `*op*` is less than 5, it maps to one of the targets. By using it as a lookup into the jump table, the processor can retrieve the address of the corresponding code block and jump to that location to execute the code.

In this case, using the jump table, the execution time is the same regardless of which case it is. The last case doesn't take any more instructions or comparisons than the first.

##### Missing Cases

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

Missing values in a jump table can be filled with the default address or done if there is no default, as shown next. This will cause the processor to jump to the proper location when `*op*` equals 3, and it attempts to jump to the corresponding location in the jump table.

####  JUMP TABLE

| target_0 |

| --- |

| target_1 |

| target_2 |

| default |

| target_4 |

##### Nonzero Bases

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

In this case, it's necessary to find a way to zero the cases. With ASCII, it's necessary to find the lowest case in the jump table that, for this example, has a value of `*a*` , or 97. When implementing a jump table for this `switch` statement, the code can use an offset, accessing values as `table[x-97]`. In the following jump table, `*target_a*` will point to case `a` of the `switch` statement.

#### JUMP TABLE

| target_a |

| --- |

| target_b |

| target_c |

| target_d |

##### Impractical Jump Tables

A compiler will use these tricks to improve code efficiency, and you can too when writing code by hand. However, sometimes a jump table just won't work. For example, consider the following code:

```
switch (x) {
    case 1:
         printf("this is the beginning."); break;
    case 1000:
        printf("this is the end."); break;
}
```

A jump table for this `switch` statement would need to have 1,000 entries and 998 of them would point to the done label. In this case, an `if/else` statement is the more efficient option.

That's not the only case where it's impractical; a larger jump table with hundreds of cases, or a table that uses an index that can't easily be zeroed or has too many gaps in the table, can be impractical. But as you both write and dissect assembly code, it's important to be able to understand these structures and how they're used.

### Continue

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

| WITH BLOCKS || WITHOUT BLOCKS |

| --- | --- |

| `do`  

`{`  

`    x--;`  

`    continue;`  

`    x++;`  

`}`  

`while (x);` || `loop:`  

`x--;`  

`goto check_condition;`  

`x++;`  

`check_condition:`  

`if (x)`  

`    goto loop;` |

| --- | --- |

In this code, the instruction `x++;` will never execute because the `continue` always causes it to be skipped. Typically, a `continue` will be located inside of an `if` statement because, otherwise, the code following it is pointless. This contrived example is designed to demonstrate how `continue` works without the complexity of `if` statements nested within a loop.

Once the code has been converted to remove code blocks, it can be translated to assembly. As before, a `goto` can be implemented using a nonconditional jump.

| CODE || X86 ASSEMBLY |

| --- | --- |

| `loop:`  

`x--;`  

`goto check_condition;`  

`x++;`  

`check_condition:`  

`if (x)`  

`    goto loop;` || `loop:`  

`sub dword [x], 1`  

`jmp check_condition`  

`add dword [x], 1`  

`check_condition:`  

`cmp dword [x], 0`  

`jne loop` |

| --- | --- |

### break

The `break` keyword also exists in some programming languages, and it instructs the processor to exit the current loop. As with `continue`, the second chunk of code in the following example will never execute, as the break would typically be inside of a conditional statement, but this is an example simply to demonstrate the break mechanism.

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

In the following example, the `break` statement would terminate the loop after the operation `x--` has been evaluated once. In this case, the `x++` statement and the loop conditional will never be executed, but again this is sample code. It shows how you'd easily put the break into a conditional.

| WITH BLOCKS || WITHOUT BLOCKS |

| --- | --- |

| `do`  

`{`  

`    x--;`  

`    break;`  

`    x++;`  

`}`  

`while (x);` || `loop:`  

`x--;`  

`goto break;`  

`x++;`  

`if (x)`  

`    goto loop;`  

`break:` |

| --- | --- |

The following example shows how the code can be converted to assembly:

| CODE || X86 ASSEMBLY |

| --- | --- |

| `loop:`  

`x--;`  

`goto break;`  

`x++;`  

`if (x)`  

`    goto loop;`  

`break:` || `loop:`  

`sub dword [x], 1`  

`jmp break`  

`add dword [x], 1`  

`cmp dword [x], 0`  

`jne loop`  

`break:` |

| --- | --- |

### &&

In higher-level languages, a conditional in an `if` statement or a loop has the potential to evaluate multiple different conditions such as a Boolean AND (`&&`). In the following example, the `if` block will be executed only if both `condition_1` and `condition_2` are true.

```
if ( condition_1 && condition_2 ) {
    code;
}
```

When converting this code to remove code blocks, it is necessary to break the multipart `if` statement into two different `if` statements. Each of these negates one of the conditionals that were included in the original `if` statement.

```
if (!condition_1) goto skip_block;
if (!condition_2) goto skip_block;
true:
code;
skip_block:
```

Once rewritten like this (without code blocks), follow the same formula to translate this to assembly.

### ||
