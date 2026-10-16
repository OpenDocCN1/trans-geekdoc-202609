
当`push ebp`指令执行时，前一个函数的基指针会被保存到栈上。随后的栈如第二个表格所示。

第三个表格显示在执行`mov ebp, esp`指令后栈的状态。栈本身没有更新，新的*`ebp`*指向调用函数的返回地址，与*`esp`*相同。

执行完这些指令后，调用函数可以将局部变量压栈。虽然这会修改*`esp`*的值，但*`ebp`*的值保持不变（表四）。这使得可以相对于固定的*`ebp`*而非更具可变性的*`esp`*来访问参数和局部变量。

##### Tearing Down a Stack Frame

为当前函数创建新的栈帧意味着丢失了调用函数的栈帧。在函数返回前，它需要撤销已做出的修改并恢复调用者的栈帧。

函数尾声位于函数末尾，完成此过程。它由以下三条指令组成：

```
mov esp, ebp
pop ebp
ret
```

此过程的第一步是移除栈上已添加的任何数据。由于数据并未真正从内存中删除，这仅涉及通过指令`mov esp, ebp`改变栈指针。此操作会将栈状态恢复至如[Table 7.11](#c07.xhtml#c07-tbl-0011)所示。

```
; function body (1)
mov esp, ebp ;(2)
pop ebp ; (3)
```

接下来，需要将基指针的值恢复为调用函数的值。回顾在前言中，这被压栈保存，因此通过指令`pop ebp`可以实现，这将栈恢复到原始状态。此时，栈已处于可返回给调用函数的正确状态。

虽然可以通过这两条指令完成栈帧撤销，x86 还提供了一个替代方案。`leave` 指令等价于以下两条指令：

```
mov esp, ebp
pop ebp
 
```

[**Table 7.11**](#c07.xhtml#R_c07-tbl-0011): Effects of function epilogue on stack

| (1)  ||     || (2) |

| --- | --- | --- |

| ADDRESS || VALUE || ADDRESS || VALUE |

| `0xefe8 (esp)` || `0x3325d321` ||     || `0xefe8` || `0x3325d321` |

| --- | --- | --- | --- | --- |

| `0xeff0` || `0x11223344` || `0xeff0` || `0x11223344` |

| `0xeff4 (ebp)` || `Old ebp` || `0xeff4 (ebp, esp)` || `Old ebp` |

| `0xeff8` || `(return address)` || `0xeff8` || `(return address)` |

| `0xeffc` || `2` || `0xeffc` || `2` |

| `0xf000` || `1` || `0xf000` || `1` |

| **(3)** ||   |

| **ADDRESS** || **VALUE** |

| `0xefe8` || `0x3325d321` |

| `0xeff0` || `0x11223344` |

| `0xeff4 (esp)` || `Old ebp` |

| `0xeff8` || `(return address)` |

| `0xeffc` || `2` |

| `0xf000` || `1` |

#### *Accessing Parameters*

栈帧设计用于简化在函数内部访问栈上的参数和其他值。使用静态*`ebp`*作为参考点简化了确定特定值在栈上的位置的过程。例如，[Table 7.12](#c07.xhtml#c07-tbl-0012)显示了使用`cdecl`约定的任何函数中栈上特定值的位置。由于*`ebp`*在函数内不移动，这些关系和偏移量始终相同。这意味着如果调用者传入了变量，第一个永远位于`ebp+8`，第二个永远位于`ebp+12`，以此类推。

[**Table 7.12**](#c07.xhtml#R_c07-tbl-0012): Stack locations for common values

| LOCATION || VALUE |

| --- | --- |

| `[ebp + 0]` || Previous frame pointer |

| --- | --- |

| `[ebp + 4]` || Function return address |

| `[ebp + 8]` || First parameter |

| `[ebp + 12]` || Second parameter |

| `[ebp + 16]` || Third parameter |

| ... || ... |

下面的示例展示了函数参数的构建和使用过程。与所有这些栈示例一样，请记住每个栈是在执行指令后显示的状态。

```
f:
    push  1   ; y
    push  2   ; x   ;(1)
    call  add
    mov   [s], eax
    pop   eax
    pop   eax
    ret
 
; int add(int x, int y) { return x+y; }
add:
       ; (2)
    push ebp
    mov  ebp, esp   ;(3)
    mov  eax, [ebp+8]     ; retrieve x from stack
    mov  edx, [ebp+12]    ; retrieve y from stack
    add  eax, edx
    mov  esp, ebp
    pop  ebp
    ret
```

[Table 7.13](#c07.xhtml#c07-tbl-0013)显示程序中第(1)、(2)和(3)点的栈内容。

[**Table 7.13**](#c07.xhtml#R_c07-tbl-0013): Stack content at points 1, 2, and 3 in the program

| (1)  ||     || (2) ||     || (3) |

| --- | --- | --- | --- | --- |

| ADDRESS || VALUE || ADDRESS || VALUE || ADDRESS || VALUE |

| `0xeff4` || `??` ||   || `0xeff4` ||   ||   || `0xeff4 (esp, ebp)` || `Old ebp` |

| --- | --- | --- | --- | --- | --- | --- | --- | --- |

| `0xeff8` || `??` || `0xeff8 (esp)` || `return address` || `0xeff8` || `return address` |

| `0xeffc (esp)` || `2` || `0xeffc` || `2` || `0xeffc` || `2` |

| `0xf000` || `1` || `0xf000` || `1` || `0xf000` || `1` |

一旦到达位置 3，根据对`cdecl`及栈帧的了解，可以确定第一个参数`x`将位于`ebp+8`处且值为2。第二个参数`y`将位于`ebp+12`处且值为1。

#### *Local Variables*

函数的局部变量存储在栈上，位于前一个帧指针（较低地址）之上。栈帧设置完成后，只需从*`esp`*减去所需的空间即可为局部变量分配空间。分配会在函数尾声自动撤销，因为栈指针会根据基指针重置。

例如，考虑以下函数：

```
void one_up(int x)
{
       int y = x + 1;
}
```

除了传入参数`x`外，该函数还定义了局部变量`y`，它将存储在栈上。下面的代码展示了该函数在 x86 架构下被翻译后的样子：

```
one_up:
    push ebp
    mov  ebp, esp
    sub  esp, 4        ; allocate space for local y (4 bytes)
    mov  eax, [ebp+8]  ; load parameter x
    inc  eax           ; x + 1
    mov  [ebp-4], eax  ; save local y
      ;stack shown here
    mov  esp, ebp
    pop  ebp
    ret
```

此程序的栈帧在[Table 7.14](#c07.xhtml#c07-tbl-0014)中显示。注意，虽然*`esp`*现在指向`0xeff4`，但*`ebp`*的值在分配局部变量后保持不变（指向调用者的保存`ebp`）。参数和局部变量都可以轻松相对于*`ebp`*访问。

[**Table 7.14**](#c07.xhtml#R_c07-tbl-0014): Stack frame of one_up program

| ADDRESS || VALUE |

| --- | --- |

| `0xeff4 (esp)` || `y` |

| --- | --- |

| `0xeff8 (ebp)` || `Old ebp` |

| `0xeffc` || `Ret address` |

| `0xf000` || `x` |

与参数一样，`cdecl` 确保局部变量在不同函数中存储位置保持一致。[Table 7.15](#c07.xhtml#c07-tbl-0015)显示了相对于*`ebp`*的局部变量位置。在反汇编中，对*`ebp`*的了解变得极其强大。

[**Table 7.15**](#c07.xhtml#R_c07-tbl-0015): Stack locations for local variables

| LOCATION || VALUE |

| --- | --- |

| `[ebp - 4]` || First local variable |

| --- | --- |

| `[ebp - 8]` || Second local variable |

| `[ebp - 12]` || Third local variable |

| ... || ... |

##### *Shortcuts*

可以单独压栈每个参数或局部变量；每次压栈操作都会更新栈指针并将值放入栈中。

相反，编译器通常会一次性分配空间再逐个写入值。例如，以下指令更少见于编译生成的代码：

```
push 1
push 2
```

更有可能被编译为以下指令：

