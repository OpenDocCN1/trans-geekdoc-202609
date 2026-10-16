
*   allowlisting, 234–235

*   AMD Omperon, 14

*   American Standard Code for Information Interchange (ASCII) 

    *   about, 54–55

    *   identifying strings, 55

    *   manipulating, 55–56

*   analyzing assembly code, 65–75

*   `AND` (`&&`), 99

*   `and` instruction, 37

*   anti-debugging 

    *   about, 212, 219

    *   debug registers, 213

    *   defeating, 215–216

    *   directory scanning, 215

    *   invalid `CloseHandle()`, 214

    *   `IsDebuggerPresent()`, 212–213

    *   lab, 216

    *   offensive, 215

    *   Read Timestamp Counter (`RDTSC`), 214

*   anti-dumping, 219

*   anti-tampering, 220

*   anti-virtualization, 219

*   API calls, 145

*   *Apple Computer v. Franklin Computer,* 242

*   application binary interface (ABI), 110

*   architectures 

    *   about, 12

    *   assembly, 7–12

    *   complex instruction set computing (CISC) architecture, 10–12

    *   computer, 5–7

    *   instruction set, 9–10

    *   microarchitectures, 9–10

    *   reduced instruction set computing (RISC) architecture, 10–12

    *   32-bit x86, 14

*   arguments, standard, 268

*   arithmetic logic unit (ALU), 6

*   arithmetic shift, 38

*   arrays, 28

*   assembly 

    *   machine code, 7–9

    *   mixing with C, 268–270

    *   syntax of, 14–15

*   assembly code 

    *   about, 8, 75

    *   analyzing and debugging, 65–75

    *   binary analysis, 65–66

    *   breakpoints, 66–67

    *   `gdb`, 68–73

    *   Immunity, 168–170

    *   lab: Shark Sim 3000, 73–74

    *   noise, 74–75

    *   segmentation faults, 73

*   assembly programs 

    *   about, 56

    *   American Standard Code for Information Interchange (ASCII), 54–56

    *   building and linking, 48–52

    *   building and running, 43–56

    *   lab: Hello World, 53–54

    *   `objdump`, 52–53

    *   output, 43–46

    *   system calls, 46–48

    *   writing, 49–52

*   Athlon 64, 14

*   AT&T syntax, 15

*   authentication, remote, 236–237

*   authentication code, 145

*   authenticity, code signing and, 230

*   automated obfuscation, 206–210

*   automatic structure recovery, 247

*   AV detection, 225

*   availability, in CIA triad, 221, 226, 227, 230, 232, 233, 235, 236, 237

*   available registers, 113

*   **B**

*   base address, 20

*   base `+` displacement addressing, 28

*   base pointer register, 22

*   base register, 22

*   based addressing, 28

*   based-index addressing, 28–29

*   bases 

    *   about, 16

    *   nonzero, 95

*   big-endian system, 20

*   binary analysis 

    *   debugging, 66

    *   dynamic analysis, 65–66

    *   static analysis, 65–66

*   binary instrumentation, 246

*   binary values, 19–20

*   bits, 17–18, 19

*   blocklisting, 235–236

*   blocks, in Interactive Disassembler (IDA), 193–194

*   branches, 78

*   `break` keyword, 97–99

*   breakpoints 

    *   about, 66–67

    *   `gdb`, 69–70

*   bridges, 6

*   building 

    *   jump tables, 92–94

    *   in Linux, 48–49

*   bytes 

    *   about, 17–18, 19

    *   copying in Cheat Engine, 188

*   **C**

*   C 

    *   connecting with x86, 262–270

    *   functions, 263–264

    *   mixing with assembly, 268–270

*   `call` instruction, 106, 110

*   call stacks, in Procmon, 158

*   caller cleanup, 112

*   calling conventions, 110–116

*   carry flag (CF), 58

*   `cdecl`, 112–116

*   central processing unit (CPU), 6

*   Cheat Engine 

    *   about, 184, 247

    *   allowlisting and, 234

    *   copying bytes, 188

    *   getting addresses, 188–189

    *   opening processes, 184–185

    *   rewriting programs, 187–188

    *   string references, 187

    *   viewing memory, 185–186

*   CIA triad, 221

*   clobbered registers, 269

*   `CloseHandle()`, 214

*   `cmp` instruction, 61–63, 80–81

*   code 

    *   iteratively annotating, 145–146

    *   signing, 230–232

*   code blocks, removing, 82

*   code-dispatch scheme, 226

*   CodeFusion, patching with, 182–184

*   Comet Cursor, 141

*   comments, in Interactive Disassembler (IDA), 196–197

*   commercial off-the-shelf (COTS) packers, 228

*   compiler boilerplate, 75

*   compilers and optimizers 

    *   about, 127, 130

    *   finding starting code, 127–130

    *   linking, 134–136

    *   optimization, 130–132

    *   stripping, 132–134

# 复杂指令集计算 (CISC) 架构 (CISC) architecture, 10–12
## 计算机架构
### 关于, 5, 9–10
### 桥梁, 6
### 中央处理器 (CPU), 6
### 内存, 6–7
### 外设, 6
### 寄存器, 6–7
# 计算机欺诈与滥用法案 (CFAA), 240–241
# 计算机支持, 为 x86, 13
## 条件码
### 关于, 57, 64
### `add` 指令, 60–61
### 进位标志 (CF), 58
### `cmp` 指令, 61–63
### `eflags` 寄存器, 58
### 影响状态标志的操作, 60–63
### 其他状态标志, 60
### 溢出标志 (OF), 59–60
### 符号标志 (SF), 59
### `sub` 指令, 61
### `test` 指令, 63
### 零标志 (ZF), 59
# 条件跳转, 79–81
# 保密性, 在 CIA 三元组中, 221, 226, 227, 230, 232, 233, 235, 236, 237
# 常量, 50
# `continue` 命令, 71–72, 96–97
# 控制标志, 58
# 控制流
## 关于, 75, 77–78
## 在复杂指令中添加注释, 145
## 条件跳转, 79–81
## 平整化, 209
## 程序计数器, 78
## 指令, 78–81
## `jmp` 指令, 78–79
# 控制单元, 6
# 约定, 调用, 110–116
# 版权法 (1976), 241, 243
# 成本, 混淆和, 205
# 计数寄存器, 22
# 破解
## 关于, 147, 177
## 使用免疫调试, 168–176
## 密钥检查器, 147–151
## 密钥生成器, 151–154
## 实验室, 155, 176–177
## 其他调试器, 167–168
## 补丁, 165–167
## Procmon 为, 155–160
## Resource Hacker, 160–165
# crackmes, 137
# CRC32 算法, 154
# 加密/解密程序, 227
# 大括号 (`{}`), 82
# 循环冗余校验 (CRC), 229–230
# D
# Dalvik, 2
# 数据
## 全局, 50–51
## 指定长度, 23–26
# Data Execution Prevention (DEP), 262
# 数据流, 145
# 数据格式
## 关于, 9
## 全局, 50–51
# 数据寄存器, 22
# 数据表示
## 二进制值, 19–20
## 位, 17–18
## 字节, 17–18
## 数字系统基数, 16–17
## 字, 17–18
# `.data` 段, 49
# 调试寄存器, 213
# 调试器
## 允许列表和, 234
## 其他, 167–168
# 调试
## 组装代码, 65–75
## 使用 Immunity, 168–176
## 永恒, 245–246
## 使用 GNU 调试器 (`gdb`), 68–73
# `dec` 指令, 35
# 反编译
## 关于, 1–2, 12
## JIT 编程语言的反编译, 2–4
## 实验室为, 4–5
## 用途, 2
# decompiling, 247
# decryptors/cryptors, 227
# 防御
## 关于, 203, 216
## 反调试, 212–216
## 混淆, 203–212
# Demand Progress, 240
# deobfuscation, 248
# Dependency Walker
## 关于, 143–144
## 允许列表和, 234
# 目的索引寄存器, 22
# 检测与防范
## 关于, 229, 238
## 允许列表, 234–235
## 阻止列表, 235–236
## 代码签名, 230–232
## 循环冗余校验 (CRC), 229–230
## 实验室, 238
## 远程身份验证, 236–237
## 运行时应用自我保护 (RASP), 232–234
# Digital Millennium Copyright Act (DMCA), 239
# 数字权益管理 (DRM), 239
# 数字签名, 150, 231
# 数字签名密钥, 150
# 方向标志 (DF), 60
# 目录扫描, 215
# 反汇编, 使用 `gdb`, 69
# `div` 指令, 36
# DMCA 研究例外, 243
# Domas, Christopher, 247
# 双字节, 18
# 双字 (`DWORD`), 18
# `do…while` 循环, 87–88
# 动态链接, 134–135
# dynStruct, 247
# E
# `eax` 寄存器, 22, 81
# `ebp` 寄存器, 22, 116, 118, 119–121, 122
# `ebx` 寄存器, 22
# `echo` 命令, 140–141
# `ecx` 寄存器, 22, 81
# `edi` 寄存器, 22
# `edx` 寄存器, 22
# `eflags` 寄存器, 23, 58
# `eip` 寄存器, 23, 78
# ELF, 48–49
# `else if` 语句, 85–87
# 编码数据在密钥中, 151
# 加密, 字符串, 207–209
# 端 ianness, 20
# Enigma, 246
# 尾声, 117
# `esi`, 22
# `esp`, 23
# 评估混淆, 205
# 示例, 示例 x86 组装指令, 35, 37, 40
# 异常, 在 Immunity 中, 173–174
# F
# fair use, 243
# 文件膨胀, 226
# 文件操作
*   文件操作，在 Procmon 中，158–160
*   标志寄存器, 23
*   `for` 循环, 90–91
*   格式, x86 汇编指令格式, 31–32
*   函数调用 
    *   关于, 75, 106, 123–125
    *   约定, 110–116
    *   x86 中的函数, 106–110
*   函数挂钩, 233
*   函数参数, 145
*   函数 
    *   C, 263–264
    *   交互反汇编器 (IDA), 194–195
    *   x86, 264–265
*   **G**
*   通用寄存器 (GPRs), 21–22
*   `GetThreadContext()`, 213
*   Ghidra, 5, 201
*   全局数据, 50–51
*   全局变量, 27
*   GNU 调试器 (`gdb`) 
    *   关于, 68
    *   使用 `gdb` 调试, 68–73
*   GNU 链接器, 49
*   `goto` 语句, 82, 84
*   guards, 219
*   **H**
*   halfword, 18
*   硬件断点, 67
*   基于哈希的白名单, 234–235
*   哈希, 218
*   十六进制编辑器, 179
*   十六进制, 16–17
*   Hotz, George, 246
*   **I**
*   IDA's Hex-Rays 反编译器, 5
*   `if` 语句, 82–83, 85–87
*   `if…else` 语句, 83–87
*   Immunity 
    *   关于, 168
    *   汇编, 168–170
    *   异常, 173–174
    *   实验室, 176–177
    *   模块, 170
    *   重写程序, 174–176
    *   运行程序, 172–173
    *   字符串, 170–172
*   `inc` 指令, 35
*   索引寻址, 28
*   间接寻址, 27–28
*   `info breakpoints` 命令, 70
*   `info` 命令, 70–71
