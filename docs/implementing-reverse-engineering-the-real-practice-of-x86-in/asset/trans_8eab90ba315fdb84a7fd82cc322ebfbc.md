
程序执行期间，一个过程会被另一个函数调用；此时使用 `CALL` 指令。使用 `CALL` 指令，指针会跳转到函数内被调用过程的代码。当 `CALL` 指令执行时，`CALL` 指令之后下一条指令的内存地址会被压入栈。被调用过程执行结束后，该内存地址会通过 `RET` 指令从栈中弹出。

**受影响的标志：** 无

**示例**

`CALL PROC_LABEL` ; 程序流程被转移到过程标签的内存位置

## [`进入`](#toc.xhtml#s92a)

指令格式：

`ENTER Storage, Level`

**含义：**

在 Intel 架构中，使用 `ENTER` 和 `LEAVE` 指令提供了另一种执行过程调用的方法。这些指令为过程创建和释放栈帧，用于存储变量和返回执行所需的指针。在 C 和 Pascal 等块结构语言中，这些指令为过程调用提供了机器语言支持。

`ENTER` 指令有 2 个操作数：

*   `Storage`：这表示为过程调用在栈上预留的字节数。
*   `Level`：也称为词法嵌套级别（从 0 到 31），它是过程调用链中过程的深度。

**受影响的标志：** 无

## [`离开`](#toc.xhtml#s93a)

指令格式：

`LEAVE`

**含义：**

该指令通过恢复 `(E)SP`/`(E)BP` 来释放为过程创建的栈帧，该栈帧用于存储变量和返回执行的指针。

**受影响的标志：** 无

## [`中断`](#toc.xhtml#s94a)

指令格式：

`INT <type>`

`type` 在 0 到 255 之间。

**含义：**

中断是一种使处理器暂停以暂时处理其他任务然后返回主任务的条件。中断是请求 CPU 注意的事件或信号。外围硬件设备使用它来访问 CPU。每当中断发生时，处理器会完成当前的一组指令，然后启动中断服务例程（`ISR`）或中断处理程序。`ISR` 是一个包含处理特定中断的一组指令的例程。该 `ISR` 告诉处理器在中断发生时该做什么。

现在，`INT` 指令允许程序显式调用中断处理程序。当调用 `INT` 指令时执行以下任务：

*   `FLAGS` 寄存器被压入栈。
*   代码段（`CS`）被压入栈。
*   `INT` 指令之后下一条指令的偏移量被压入栈。
*   `IP`（指令指针）从绝对内存地址加载，该地址是中断类型乘以 4 的倍数。如果 `INT` 为 8，则 `IP`（指令指针）将从 8 * 4 = 32 十进制 = 0x00020 内存位置读取。
*   代码段将是下一个 WORD 位置。`CS` 将为 0x00022（0x00020 + 2）。
*   重置 `TF` 陷阱标志（`TF`）和 `IF` 中断标志（`IF`）。

**受影响的标志：** `IF`、`TF`

## [`中断溢出`](#toc.xhtml#s95a)

指令格式：

`INTO`

**含义：**

`Interrupt Overflow`（`INTO`）：如果溢出标志（`OF`）被置位，则该指令会引发溢出异常。如果 `OF` 未被置位，则指令执行继续而不引发异常。这有助于检查溢出条件。当调用 `INT` 指令时执行以下任务：

*   `FLAGS` 寄存器被压入栈。
*   `CS`（代码段）被压入栈。
*   `INT` 指令之后下一条指令的偏移量被压入栈。
*   `IP`（指令指针）从绝对内存地址加载，该地址是中断类型乘以 4 的倍数。
*   如果溢出条件为 `INT` 4，则 `IP`（指令指针）将从 4 * 4 = 16 十进制 = 0x00010 内存位置读取。
*   代码段将是下一个 WORD 位置。`CS` 将为 0x00012（0x00010 + 2）。
*   将中断标志和陷阱标志重置为 0。

**受影响的标志：** `IF`、`TF`

## [`中断返回`](#toc.xhtml#s96a)

指令格式：

`IRET`

**含义：**

`Interrupt Return`（`IRET`）：该指令用于结束中断服务例程（`ISR`）或中断处理程序并将执行返回到被中断的程序。当中断服务例程（`ISR`）被调用时，指令指针、代码段和标志寄存器会被压入栈。从 `ISR` 返回时，指令指针、代码段和标志会从栈中恢复以继续执行被中断的程序。

**受影响的标志：** `AF`、`CF`、`DF`、`IF`、`ZF`、`SF`、`TF`、`PF`

## [`循环`](#toc.xhtml#s97a)

指令格式：

`LOOP DESTINATION`

**含义：**

在 `LOOP` 指令中，`(E)CX` 寄存器减 1。如果 `(E)CX` 寄存器中的新值非零，则会跳转到指令中提到的目标。如果 `(E)CX` 寄存器递减且 `ECX` 等于 0，则不会采取任何操作，并且会执行 `LOOPE` 指令之后的下一条指令。

**受影响的标志：** 无

**示例**

```
LOOPE MEM_LOC     ; Program will jump to the memory location if ECX is non-zero
                  ; after decrementing
```

## [`循环相等`](#toc.xhtml#s98a)

指令格式：

`LOOPE DESTINATION`

**含义：**

在 `LOOPE` 指令中，`(E)CX` 寄存器减 1。如果 `(E)CX` 寄存器中的新值非零且 `ZF` 标志被置为 1，则会跳转到指令中提到的目标。如果 `(E)CX` 寄存器递减且 `ECX` 等于 0，则不会采取任何操作，并且会执行 `LOOPE` 指令之后的下一条指令。

**受影响的标志：** 无

**示例**

```
LOOPE MEM_LOC     ; Program will jump to the memory location if ECX is non-zero
                  ; after decrementing and ZF=1 due to the previous instruction
```

## [`循环不相等`](#toc.xhtml#s99a)

指令格式：

`LOOPNE DESTINATION`

**含义：**

在 `LOOPNE` 指令中，`(E)CX` 寄存器减 1。如果 `(E)CX` 寄存器中的新值非零且 `ZF` 标志被置为 0，则会跳转到指令中提到的目标。如果 `(E)CX` 寄存器递减且 `ECX` 等于 0，则不会采取任何操作，并且会执行 `LOOPNE` 指令之后的下一条指令。

**受影响的标志：** 无

**示例**

```
LOOPNE MEM_LOC    ; Program will jump to the memory location if ECX is non-zero
                  ; after decrementing and ZF=0 due to the previous instruction
```

## [`测试`](#toc.xhtml#s100a)

指令格式：

`TEST DESTINATION_OPERAND SOURCE_OPERAND`

**含义：**

该指令在源操作数和目标操作数之间执行逻辑 AND。与 `AND` 指令不同，`TEST` 指令不会更新任何操作数。它在不保存结果的情况下更新标志。该指令用于在不改变其值的情况下检查寄存器是否为零。

**受影响的标志：** `SF`、`ZF` 和 `PF`

**示例**

```
TEST EAX, 01H    ; IF EAX=01H
                 ; 01H AND 01H = 01H (non-zero value)
                 ; Result is non-zero value, ZF is not set, ZF=0
TEST EAX, 02H    ; IF EAX=01H
                 ; 01H AND 02H = 00H (zero value)
                 ; Result is zero value, ZF is set, ZF=1
TEST EAX, EAX    ; if EAX is equal to 0, set ZF to 1
```

## [`分支指令`](#toc.xhtml#s101a)

这包括有助于控制代码流程的指令。x86 中有两种类型的跳转：

*   `Unconditional jump`：指令指针跳转到提及的代码路径。
