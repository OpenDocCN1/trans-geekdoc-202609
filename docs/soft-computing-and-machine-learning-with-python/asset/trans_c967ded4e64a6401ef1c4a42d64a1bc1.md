

# 用于自动提取...模式的高效平台 ... 289

算法 6 显示了我们示例中使用的另一种模式检测器（Pattern Detector）。它将一个 CALL 指令之后的指令（我们称之为 call post）识别为模式。在这种情况下，与模式相关的个体（individual）不是该指令所属的函数，而是被调用的函数。同样，我们还指定了 CALL 之前的指令模式，称为 call pre，未在算法中显示。这两种模式的思路是：函数返回值的用法（call post）以及推入其模式的代码（call pre）可能对于推断函数签的的类型（返回类型和参数类型）具有价值。

## 算法 6：识别 call post 模式的模式检测器规则。

```
Function CALL_Post_pattern_detector(instruction)
  if instruction is CALL id_func then
    begin_instruction ← instruction
    for i = 0 to MaxSize + MaxOffset do
      instruction ← next(instruction)
    end
    return(id_func, (begin_instruction, instruction))
  end if
  return null
```

此时，该模块已提取了三种类型的模式：ret 模式（包括返回语句的汇编代码）、call pre 模式和 call post 模式（代表调用函数前后的代码）。每种模式都可能包含大量的连续二进制指令。然而，我们可能对大模式内部的一小部分连续指令感兴趣。因此，二进制提取模式（Binary Extraction Pattern）被设计为将找到的模式划分为子模式集合（原始模式的不同划分）。

获取子模式的算法由图 1 所示的 Max Size 和 Max Offset 参数化。该算法从长度为 1 条指令的子模式（size = 1）开始，其值逐渐增加，直到达到多达 Max Size 条的连续指令。此外，还会提取其他子模式，并在模式检测器检测到的指令与子模式之间留出偏移指令。上述的算法适用于 offset = 0。相同的算法也适用于 offset = 1 和 offset = -1（即检测到的指令之前和之后的第一条指令，它们不包含在子模式中）。offset 的绝对值一直增加到 Max Offset。

图 2 显示了 4 个示例子模式。从一个 call pre 模式中，显示了 size = 5 且 offset = 0，以及 size = 2 且 offset = -2 的子模式。从另一个 call post 模式中，图 2 显示了 size = 3 且 offset = 2，以及 size = 3 且 offset = 1 的子模式。

| mov edx, [ebp+var_8] | Size: 2 |
|---|---|
| push edx | Relative offset: -2 |
| mov eax, [ebp+var_C] | Pattern type: call pre |
| push eax | |
| call func710 | |
| add sp, 8 | |
| movzx ecx, [ebp+lb_1] | Size: 3 |
| push eax | Relative offset: +1 |
| call func1195 | Pattern type: call post |
| | |

**图 2：** 从 2 个模式中提取的 4 个子模式的示例。

模式检测器要完成的最后一个任务是将个体与其模式关联，并通过写入出现发生表（Occurrences Table）使这种关联显式化。这一过程产生与个体检测器（算法 4）发现的个体数量相等的表格行，并将它们与模式检测器函数（算法 5 和 6）为每个个体找到的每个子模式行进行关联。

## 模式生成器 (Pattern Generator)

子模式太具体了。例如，MOV eax,5 和 MOV ax,1 子模式被识别为两个不同的模式。然而，对于检测一个函数是否返回了值，它们可以被视为同一个模式，即字面量（literal）被赋值给了累加器寄存器（即 MOV <generic ax>,<literal>模式）。为此，模式生成器模块的目标是允许我们通过泛化它们来减少子模式的数量。

在二进制模式提取中，对汇编指令进行泛化（或归一化）的必要性之前的工作中已经被发现。在 [6] 中，*通配符* 匹配任意一条指令，而操作数的缺失意味着任何值。在后续工作中，他们还识别了忽略内存地址和字面值的必要性 [7]。Bao 等人提出的泛化使用正则表达式来泛化字面量甚至指令助记符 [5]。另一种更粗粒度的归一化忽略了所有汇编指令的操作数 [15]。

为了识别通用平台的泛化需求，我们分析了第 2 节描述的反汇编场景。这些泛化的某些示例所示表 1。首先，用户应该能够泛化指令操作数，包括字面量、寄存器、变量和内存地址。其次，平台应该允许泛化具有相同目的的指令。最后，用户可能需要泛化变长指令的子模式，例如函数调用者和被调用者的尾（epilogues）。

### 表 1：子模式的泛化示例

| 操作数 | 示例模式 | 泛化 |
|---|---|---|
| | mov 5,eax | mov <literal>;<generic ax> |
| | mov [exc],al | mov <exc>;<register> |
| | movsd xmm0,var_0 | movsd xmm0,<var> |
| | mov edx,eax,al | mov edx,<generic ax>;<any> |
| | call func1493 | call <address> |
| 助记符 | movzx eax,al | movss [esp+54h+var_2],xmm0 | <mov>[esp+54h+var_2],xmm0 |
| | movsd xmm0,var 3 | <mov> xmm0,<var> |
| | mov edx,[ebp+var_4] | <mov> edx,<var> |
| | movsx ecx,[ebp+var_5] | <mov> ecx,<var> |
| 指令组 | pop esp; mov esp,ebp; pop retn | <callee epilogue> |
| | mov esp,ebp; pop esp; retn | <callee epilogue> |
| | pop ebp; retn | <callee epilogue> |
| | call func123; add esp,8 | <caller epilogue> |
| | call func123 | <caller epilogue> |

### 表 2：用于预测函数返回类型的生成的示例数据集

| (返回模式) | (调用模式) | 返回类型 |
|---|---|---|
| <mov> <generic ax>; | <callee epilogue>; | target |
| <caller epilogue>; | ... | ... |
| func.730 | 0 | int |
| func.1195 | 1 | double |
| func.295 | 0 | long long |

# 用于自动提取...模式的高效平台 ... 291

## 分类器 (Classifier)

该模块旨在计算每个个体的分类器变量（即因变量）。输入是高层程序的表示；输出是每个个体与分类器变量值之间的映射。这些关联由用户用分类规则（Classification Rules）描述。

算法 8 显示了我们示例中的分类规则。我们遍历程序中的语句。对于每个函数，我们将其标识符与返回类型关联，返回类型是我们问题中的分类器变量（我们预测函数的返回类型）。

### 算法 8：将每个函数与其返回类型关联的分类规则。

```
function .classification(program)\ individuals ← {}
for all stmt in program do
  if stype is type_return id_func ((type_arg id_arg)* then
    individuals ← individuals[id_func ↦ type_return]
  end
end for
return individuals
```

## 数据集生成器 (Dataset Generator)

最后，数据集生成器从发生表（第 3.3 节）和个体分类（第 3.4 节）生成数据集：每个个体一行，每个子模式一列（泛化的或未泛化的），另一行作为分类器变量。数据集中的单元格是布尔值，表示子模式在个体中的出现情况。分类器或目标单元格可能有不同的值。表 2 显示了一个示例数据集。

# 处理二进制文件

如所述，该平台有两种工作模式。很多时候，我们没有用于生成原生代码的高层源程序，我们感兴趣在二进制文件中寻找模式。这种场景的不同示例包括作者身份、编译器和恶意软件检测。

## 算法 7：move 指令的模式泛化。

```
Function MOVE.generalization(instruction)
  if instruction.mnemonic in [mov, movzx, movsd, movsx]
    and instruction.operands[1].type = register
    and instruction.operands[1].value in [eax, ax, ah, al] then
    instruction.mnemonic ← <mov>
    instruction.operands[1].value ← <generic ax>
    instruction.operands[2].value ← <any>
  end
  return (instruction, next(instruction))
```

