
# 理解基石编程概念

让我们从理解一些基石编程概念开始。随着计算机变得更强大、更普及，创建计算机软件的过程和方法也在增长和变化。请记住，没有一种方法必然优于另一种：正如我们在下一节将看到的，高级语言（如 C）允许程序员比低级语言（如汇编语言）更快地编写代码，但用汇编语言编写的代码可能效率高得多。哪种更好取决于项目的需求。

## 机器码、源代码和汇编器

**机器码**（也称为机器语言）是由 CPU 直接执行的软件。机器码依赖于 CPU；它是一系列 1 和 0，转换为 CPU 能够理解的指令。**源代码**是以文本编写的计算机编程语言指令，必须在 CPU 执行前翻译成机器码。高级语言包含类英语的指令，例如 `printf`（格式化打印）。

**汇编语言**是一种低级计算机编程语言。汇编语言指令是简短的助记符，如 `ADD`、`SUB`（减法）和 `JMP`（跳转），它们与机器语言指令一一对应。**汇编器**将汇编语言转换为机器语言。**反汇编器**尝试将机器语言转换回汇编语言。

## 编译器、解释器和字节码

**编译器**获取源代码（如 C 或 Basic），并将其编译为机器码。

以下是一个 C 语言“Hello World”示例程序：

```c
int main()
{
    printf("hello, world");
}
```

编译器（如 `gcc`，即 GNU 编译器套件，参见 [http://gcc.gnu.org](http://gcc.gnu.org)）将这种高级语言翻译成机器码，并将结果保存为可执行文件（如 `hello-world.exe`）。一旦编译完成，机器语言就由 CPU 直接执行。`hello-world.exe` 只编译一次，之后可运行无数次。请注意，执行（即运行）程序的过程称为**运行时**。

**解释型语言**与编译型语言不同：解释型代码（如 Shell 代码）在每次运行程序时即时编译。以下是用解释型脚本语言 Python 编写的“Hello World”程序示例（参见 [https://www.python.org](https://www.python.org)）：

```python
#!/usr/local/bin/python
print("Hello World!")
```

此代码保存为 `hello-world.py`。每次运行时，Python 解释器（在前面的代码中位于 `/usr/local/bin/python`）将 Python 指令翻译成机器语言。如果 `hello-world.py` 运行 100 次，它将被编译 100 次（而 `hello-world.exe` 只编译一次）。

**字节码**（如 Java 字节码）也是解释型代码。字节码作为一种中间形式存在（从源代码转换而来），但在 CPU 上运行前仍必须转换为机器码。Java 字节码是与平台无关的代码，由 Java 虚拟机（JVM，参见[第 4 章](#Ch004_107-223_B9780443187346000076_1.xhtml)，领域 3：安全架构与工程，了解更多关于 Java 字节码的信息）转换为机器码。

## 过程式语言和面向对象语言

**过程式语言**（也称为面向过程语言）使用子程序、过程和函数。示例包括 Basic、C、Fortran 和 Pascal。**面向对象语言**尝试通过使用结合了方法和数据的对象来模拟现实世界。示例包括 C++、Ruby 和 Python；更多信息请参见下文的“面向对象设计与编程”部分。过程式语言中的函数等同于面向对象语言中的方法。

以下代码展示了来自 BSD 文本游戏 *Trek* 的 `ram()` 函数的开头，用 C 语言（一种过程式语言）编写：

```c
void ram(ix, iy)
int ix, iy;
{
    int i;
    char c;
    printf("\07RED ALERT\07: collision imminent\n");
    c = Sect[ix][iy];
    switch (c)
    {
        case KLINGON:
            printf("%s rams Klingon at %d,%d\n", Ship.shipname, ix, iy);
            killk(ix, iy);
            break;
        case STAR:
        case INHABIT:
            printf("Yeoman Rand: Captain, isn't it getting hot in here?\n");
            sleep(2);
            printf("Spock: Hull temperature approaching 550 Degrees Kelvin.\n");
            lose(L_STAR);
        case BASE:
            printf("You ran into the starbase at %d,%d\n", ix, iy);
            killb(Ship.quadx, Ship.quady);
            /* don't penalize the captain if it wasn't his fault */[\[2\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0015)
```

此 `ram()` 函数还调用了其他函数，包括 `killk()`、`killb()` 和 `lose()`。

接下来是一个面向对象的 Ruby 示例（参见 [http://ruby-lang.org](http://ruby-lang.org)），用于文本冒险游戏，创建了一个名为 `Verb` 的类，然后创建了多个 `Verb` 对象。正如我们将在下文的“面向对象设计与编程”部分学到的，对象从其父类继承特性。

```ruby
class Verb
    attr_accessor :name, :description
    def initialize(params)
        @name = params[:name]
        @description = params[:description]
    end
end

# Create verbs
north = Verb.new( :name => "Move north", :description => "Player moves to the north" )
east = Verb.new( :name => "Move east", :description => "Player moves to the east" )
west = Verb.new( :name => "Move west", :description => "Player moves to the west" )
south = Verb.new( :name => "Move south", :description => "Player moves to the south" )
xyzzy = Verb.new( :name => "Magic word", :description => "Player teleports to another location in the cave" )[\[3\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0020)
```

请注意，编码本身不可测试；这些示例仅用于说明目的。

## 第四代编程语言

**第四代编程语言**（4GL）是旨在通过自动创建计算机编程代码来提高程序员效率的计算机语言。它们被称为“第四代”，因为可以将其视为计算机语言进化的第四步：

*   第一代语言：机器码
*   第二代语言：汇编语言
*   第三代语言：COBOL、C、Basic
*   第四代语言：ColdFusion、Progress 4GL、Oracle Reports

第四代语言倾向于专注于图形用户界面（GUI），通过拖放元素，然后根据结果生成代码。4GL 语言通常专注于数据库、报表和网站的创建。

## 集成开发环境

**集成开发环境**（IDE）通过为程序员提供一个可以执行以下功能的单一界面来提高生产力：

*   编辑
*   调试
*   语法检查和高亮
*   编译
*   解释
*   版本控制

Microsoft 的 `Visual Studio Code` 是最流行的 IDE 之一，如[图 9.1](#Ch009_459-508_B9780443187346000088.xhtml#f0010)所示。

![图 9.1 Microsoft 的 Visual Studio [4]。](images/B9780443187346000088/f09-01-9780443187346.jpg)

[图 9.1](#Ch009_459-508_B9780443187346000088.xhtml#B-f0010) Microsoft 的 Visual Studio [[4\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0025)。

## 计算机辅助软件工程 (CASE)
