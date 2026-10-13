
大多数编程语言提供完全托管的内存分配并限制对正确边界的访问，但出于效率或灵活性的原因，有时也因为遗留代码的惯性，其他语言（主要是 C 和 C++）将内存管理的工作交给了程序员。当程序员承担这项工作时——即使是经验丰富的程序员——也很容易出错，尤其是当代码变得复杂时，会产生严重的漏洞。正如前面描述的算术缺陷一样，当违反内存管理协议的行为未被捕获并继续悄无声息地发生时，危害最大。

本节重点关注直接管理和访问内存且缺乏内置保护机制的代码的安全方面。代码示例将使用原始 C 标准库的经典动态内存函数，但这些经验普遍适用于许多提供类似功能的变体。

### 内存管理

指针允许通过地址直接访问内存，它们或许是 C 语言最强大的特性。但就像使用任何电动工具一样，采取负责任的安全预防措施来管理随之而来的风险非常重要。软件在需要时分配内存，在可用边界内工作，在不再需要时释放内存。任何超出这种空间和时间约定的访问都会产生意外后果，这也是漏洞产生的根源。

C 标准库为大型数据结构，或在编译时无法确定大小的数据结构提供动态内存分配。这部分内存从*堆*分配——进程地址空间中用于提供工作内存的一大块区域。C 程序使用 `malloc(3)` 分配内存，不再需要时，通过调用 `free(3)` 释放每次分配以供重用。这些分配和释放函数有许多变体；为简单起见，我们将重点关注这两个，但这些思想适用于任何直接管理内存的代码。

当大量代码共享一个最终被释放的数据结构，但指针的副本仍然保留并被错误使用时，很容易发生释放后访问。内存被回收后，任何对这些旧指针的使用都违反了内存访问完整性。另一方面，使用后忘记释放内存有耗尽堆并导致内存耗尽的风险。以下代码片段展示了堆内存的基本正确用法：

```
uint8_t *p;
// Don't use the pointer before allocating memory for it.
p = malloc(100);  // Allocate 100 bytes before first use.
p[0] = 1;
p[99] = 123 + p[0];
free(p);          // Release the memory after last use.
// Don't use the pointer anymore.
```

这段代码在分配和释放调用之间、分配内存边界内访问内存。

在实际使用中，分配、内存访问和释放可能分散在代码各处，使得始终正确执行这套流程变得棘手。

### 缓冲区溢出

当代码访问预期目标缓冲区之外的内存位置时，会发生*缓冲区溢出*（或称为*缓冲区越界*）。弄清其含义非常重要，因为术语容易混淆。*缓冲区*是内存中任意区域的通用术语：数据结构、字符串、数组、对象或任意类型的变量。*访问*是读或写内存的统称。这意味着缓冲区溢出涉及在预期内存区域之外进行读或写，尽管“溢出”更自然地描述写入行为。虽然读和写的效果从根本上不同，但将它们放在一起思考有助于理解问题。

缓冲区溢出不局限于堆内存，也可能发生在任何类型的变量上，包括静态分配和栈上的局部变量。所有这些都可能以任意方式修改内存中的其他数据。非预期的越界写入几乎可以改变内存中的任何内容，聪明的攻击者会优化此类攻击以试图造成最大破坏。此外，缓冲区溢出漏洞可能意外读取内存，可能向攻击者泄露信息，或以其他方式导致代码行为异常。

不要低估准确做到显式内存分配、边界内访问和释放未使用存储的难度和重要性。包含异常处理在内的简单分配、使用和释放模式是最好的，这能确保释放操作永远不会被跳过。当一个组件的分配将引用移交给其他代码时，将后续释放内存的责任明确划分给接口的一方至关重要。

最后，要认识到即使在完全范围检查、带垃圾回收的语言中，你仍可能遇到麻烦。任何直接操作内存中数据结构的代码都可能犯下等同于缓冲区溢出问题的错误。例如，考虑操作字节字符串，如 Python 字节数组中的 TCP/IP 数据包。读取内容和进行修改涉及计算数据偏移量，即使不发生数组越界访问，也可能存在漏洞。

### 示例：内存分配漏洞

让我们看一个展示动态内存分配出错危险的示例。我将使这个示例简单直接，但在实际应用中，关键代码片段往往是分离的，使得这些缺陷更难被发现。

#### 简单数据结构

此示例使用一个表示用户账户的简单 C 数据结构。该结构包含一个标志（用户为管理员时设置）、用户 ID、用户名和设置集合。这些字段的语义对我们无关紧要，除了 `isAdmin` 字段非零时会赋予无限授权（使该字段成为极具吸引力的攻击目标）：

```
#define MAX_USERNAME_LEN 39
#define SETTINGS_COUNT 10
typedef struct {
  bool isAdmin;
  long userid;
  char username[MAX_USERNAME_LEN + 1];
  long setting[SETTINGS_COUNT];
} user_account;
```

下面是创建用户账户记录的函数：

```
user_account* create_user_account(bool isAdmin, const char* username) {
  user_account* ua;
  if (strlen(username) > MAX_USERNAME_LEN)
    return NULL;
  ua = malloc(sizeof (user_account));
  if (NULL == ua) {
    fprintf(stderr, "malloc failed to allocate memory.");
    return NULL;
  }
  ua->isAdmin = isAdmin;
  ua->userid = userid_next++;
  strcpy(ua->username, username);
  memset(&ua->setting, 0, sizeof ua->setting);
  return ua;
}
```

第一个参数指定用户是否为管理员。第二个参数提供用户名，其长度不得超过指定的最大长度。全局计数器 `userid_next`（声明未显示）提供顺序唯一 ID。所有设置的值初始为零，除非错误导致返回 `NULL`，否则代码返回指向新记录的指针。请注意，代码在分配前检查 `username` 字符串的长度，因此仅在内存将被使用时才进行分配。

#### 写入索引字段

创建记录后，可以使用以下函数设置所有设置的值：

**易受攻击的代码**

```
bool update_setting(user_account* ua,
                    const char *index, const char *value) {
  char *endptr;
  long i, v;
  i = strtol(index, &endptr, 10);
  if (*endptr)
    return false;  // Terminated other than at end of string.
  if (i >= SETTINGS_COUNT)
    return false;
  v = strtol(value, &endptr, 10);
  if (*endptr)
    return false;  // Terminated other than at end of string.
  ua->setting[i] = v;
  return true;
}
```
