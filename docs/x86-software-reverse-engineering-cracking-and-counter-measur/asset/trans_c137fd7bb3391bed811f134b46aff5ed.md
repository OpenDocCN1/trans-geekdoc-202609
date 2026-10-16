
在 `if` 语句中，另一种选择是使用布尔或（`||`）组合多个条件。下面的伪代码展示了这一点：

```
if ( condition_1 || condition_2 ) {
    code;
}
```

当去除代码块时，布尔或会被拆分为两个 `if` 语句，但这些 `if` 语句的形式与布尔与（`&&`）不同：

```
if (condition_1) goto true;
if (!condition_2) goto skip_block;
true:
code;
skip_block: 
```

布尔或语句为真，只要两个条件中任意一个为真。在前面的例子中，第一个 `if` 语句使用原始 *`condition_1`*，因为它为真，所以不需要评估第二个条件，直接跳转到 *`true`* 标签。

如果该条件为假，代码会继续评估 *`condition_2`*。该条件取反，跳转到 `if` 语句末尾。如果 *`condition_2`* 为真，代码会顺流进入 *`true`* 块；否则，它会跳过 `if` 语句。

## Stack

在汇编中，栈用于存储几种不同类型的数据，包括：

*   局部变量

*   暂时空间

*   参数和函数调用

栈得名于它是一种后进先出（LIFO）结构，类似于纸张堆。这个概念与编程的控制流相匹配，栈在各种架构中非常常见。

栈拥有一个 *栈指针*，指示栈的顶部。一些专门用于栈操作的指令将在本节中详细探讨。 *push* 将新值存储在栈的当前顶部，并更新栈指针以指示新的栈顶（相当于在栈上放入一张新的纸）。 *pop* 将栈顶的值移动到寄存器或内存地址，并更新栈指针，使其指向栈中位于该值下方的新顶部（相当于从栈上取下一张纸）。

### 栈的工作原理

当新函数被调用时，程序栈会从基地址向上增长，当函数返回时则向下缩小。栈越高，地址越小；栈越低，地址越大。

### x86 栈

x86 栈并不是处理器中独立的或单独的内存空间。它是应用程序为其分配并在程序内存中与其他数据并存的内存区域。例如，下面的代码会分配 128 字节供栈使用：

```
section .data
times 128 db 0
stack equ $-4
```

在 x86 中，有两个寄存器用于管理栈：

*   `esp`：栈指针保存栈顶部的地址。

*   `ebp`：基指针保存栈帧的基地址。

逻辑上，栈应该向上增长，在 x86 中这意味着地址递减，如 [Figure 7.2](#c07.xhtml#c07-fig-0002) 所示。可以把它想象成一个倒置的温度计，0 在顶部，最大值在底部。

![Figure 7.2: Stack address growth](images/c07f002.png)

[**Figure 7.2**](#c07.xhtml#R_c07-fig-000.<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>
