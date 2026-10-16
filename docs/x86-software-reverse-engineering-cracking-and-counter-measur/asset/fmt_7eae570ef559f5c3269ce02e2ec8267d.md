
The branch occurs at the `jne` (jump not equal to) instruction in the second-to-last line. The previous instruction is a `cmp`, which checks if the loop counter is equal to 5 and sets the status flags accordingly. If the loop counter does not equal 5, the jump triggers, and the `eip` register is set to the address indicated by `loop` , beginning another iteration. If the loop counter does equal 5, the jump is not taken, and the processor continues on to the `done` label.

## Logic Constructs in x86

C/C++ and similar high-level languages have multiple logic constructs that cause nonsequential code execution. Some examples include the following:

```
if (…) { … }
if (…) { … } else { … }
if (…) { … } else if (…) { … } else { … }
while (…) { … }
do { … } while (…);
for (…; …; …) { … }
switch (…) { … }
```
In assembly, these logical constructs are written using a combination of comparison (`cmp`) and jump (`jmp`, `je`, `jne`, `jl`, `jle`, `jg`, and `jge`) instructions. When code is compiled, the compiler will automatically perform the translation to assembly code.

When writing assembly code, it is necessary to perform the conversion from high-level concepts to assembly manually. Or when reasoning about other people's code, it is essential to be able to understand how these structures look in assembly. To build up this recognition, focus on how you would take these higher-level language concepts and translate them to assembly. Accomplishing this is a two-step process:

1. **Remove code blocks:** Rewrite code replacing logical constructs with `goto` statements.

2. **Assemble:** Rewrite the program in assembly.

### if (…) {…}

An `if` statement is one of the simplest high-level logical constructs. With code blocks, it looks like the following:

```
if (condition)
{
       code_if_true;
}
```

The first step is to remove code blocks. Code blocks are code that is nested inside curly braces: {}. When removing these code blocks, use `goto` statements, which tell code where to jump for execution. Not all higher-level languages have a concept of a `goto`, but focus on this as pseudocode and leverage the `goto`. The following code is the same `if` statement written without code blocks:

```
if (!condition)
       goto skip_block;
 
code_if_true;
 
skip_block:
```

Note that, in this version, the condition is inverted. This is because the jump past the `if` block occurs only if the condition is false, while the `if` block of an `if` statement specifies what happens if the condition is true. Removing code blocks will always involve inverting the condition.

Converting this from pseudocode to a functional application requires replacing *`condition`* and *`code_if_true`* with actual code.

| WITH BLOCKS || WITHOUT BLOCKS |

| --- | --- |

| 

```
if (x==5)

{

   x++;
   y=x;

}
```

 || 

```
if (x!=5)

     goto skip_block;


x++;

y=x;


skip_block:
```

 |

| --- | --- |

| --- | --- |

After removing the code blocks, converting the code to assembly is much easier. Then, this can be directly mapped to their x86 equivalents.

| CODE || X86 ASSEMBLY |

| --- | --- |

| `if (x!=5)`  

`     goto skip_block;`  

`x++;`  

`y=x;`  

`skip_block:` || `cmp dword [x], 5`  

`jne skip_block`  

`inc dword [x]`  

`mov eax, [x]`  

`mov [y], eax`  

`skip_block:` |

| --- | --- |

### if (…) { … } else { … }

Adding an `else` statement to an `if` construct increases the complexity and the required number of jumps. In addition to skipping over the `if` block if the condition evaluates as false, an `if (…) { … } else { … }` construct jumps over the `else` block after executing the code in the if block.

The following samples show how this logical construct appears with and without blocks:

| WITH BLOCKS || WITHOUT BLOCKS |

| --- | --- |

| `if (condition)`  

`{`  

`    code_if_true;`  

`}`  

`else`  

`{`  

`    code_if_false;`  

`}` || `if (!condition)`  

`    goto false_block;`  

`code_if_true;`  

`goto skip_block;`  

`false_block:`  

`code_if_false;`  

`skip_block:` |

| --- | --- |

Note that the code uses two different labels in its `goto` statements. The label *`false_block`* is used to skip over the `if` block if the condition is false, while the label *`skip_block`* is used to jump past the `else` block after executing the `if` block. Just like before, invert the conditional statement when rewriting code without blocks.

Replacing the pseudocode with actual code yields the following with and without code blocks:

| WITH BLOCKS || WITHOUT BLOCKS |

| --- | --- |

| `if (x)`  

`{`  

`    x++;`  

`}`  

`else`  

`{`  

`    x--;`  

`}` || `if (!x)`  

`    goto false_block;`  

`x++;`  

`goto skip_block;`  

`false_block:`  

`x--;`  

`skip_block:` |

| --- | --- |

As before, removing the blocks makes it easier to convert the high-level code into assembly code.

| CODE || X86 ASSEMBLY |

| --- | --- |

| `if (!x)`  

`    goto false_block;`  

`x++;`  

`goto skip_block;`  

`false_block:`  

`x--;`  

`skip_block:` || `cmp dword [x], 0`  

`je false_block`  

`inc dword [x]`  

`jmp skip_block`  

`false_block:`  

`dec dword [x]`  

`skip_block:` |

| --- | --- |

#### *if (…) { … } else if { … } else { … }*

`if` statements can be made more complex and evaluate multiple different conditions. The following demonstrates an `if` statement with `else if` and `else` with and without blocks. But the process still stays the same. Invert the condition, and add `goto`s.

| WITH BLOCKS || WITHOUT BLOCKS |

| --- | --- |

| `if (condition_1)`  

`{`  

`    code_if_1;`  

`}`  

`else if (condition_2)`  

`{`  

`    code_if_2;`  

`}`  

`else`  

`{`  

`    code_if_false;`  

`}` || `if (!condition_1)`  

`    goto test_2;`  

`code_if_1;`  

`goto skip_block;`  

`test_2:`  

`if (!condition_2)`  

`    goto false_block;`  

`code_if_2;`  

`goto skip_block;`  

`false_block:`  

`code_if_false;`  

`skip_block:` |

| --- | --- |

Note that, once again, converting to a blockless version requires flipping the conditions. The strictly less than statements become greater than or equal to 1. The following example shows how this code is then easily translated to assembly:

| CODE || X86 ASSEMBLY |

| --- | --- |

| `if (score<=70)`  

`    goto test_2;`  

`grade='a';`  

`goto skip_block;`  

`test_2:`  

`if (score<=50)`  

`    goto false_block;` || `cmp dword [score], 70`  

`jle test_2`  

`mov byte [grade], 'a'`  

`jmp skip_block`  

`test_2:`  

`cmp dword [score], 50`  

`jle false_block` |

| --- | --- |

| `grade='b';`  

`goto skip_block;`  

`false_block:`  

`grade='c';`  

`skip_block:` || `mov byte [grade], 'b'`  

`jmp skip_block`  

`false_block:`  

`mov byte [grade], 'c'`  

`skip_block:` |

### do { ... } while (...);

Higher-level programming languages have a number of different loop structures, each of which works slightly differently. A `do…while` loop is guaranteed to perform at least one iteration before evaluating the condition that would terminate the loop. The following is an example of a `do…while` loop with blocks:

```
do
{
    code;
}
while (condition);
```
