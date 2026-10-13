
作为改进，我们可以存储学生人数及其各自的年龄，仅在请求时计算平均年龄。但这仍然很笨拙。你能想出更好的设计吗？

正如你可能意识到的，无需在类中存储学生人数，因为这可以通过计数函数得出。这避免了每当有人加入或离开班级时都要更新班级规模。此外，甚至无需存储学生的个别年龄。计算机系统拥有内置时钟，可访问当前日期。如果我们存储学生的出生日期，则可通过适当的日期减法算法，在请求时由系统推导出任何学生的年龄。这样，我们就不必担心随着学生长大一岁而更新他们的年龄。

有时，所需的不是当前年龄，而是某一特定日期的年龄（例如入学日期、未来体育比赛的年龄分组）。在这些需要为每个人提供单一、稳定年龄的情况下，存储年龄可能是合适的。

在考虑使用逻辑推理的推导示例之前，请注意*命题*与*句子*的区别。命题由陈述句断言，且永远是真或假（不能两者皆是）。同一命题可由不同句子断言，例如“巴黎是法国的首都”和“法国的首都是巴黎”。

虽然人类能以非常复杂的方式处理深层含义，但计算机完全是字面理解的：它们处理的是句子而非其含义。如果我们希望计算机建立对我们显而易见的联系，必须为其显式提供建立此类联系所需的背景知识或规则。

假设关于兄弟关系和父母关系的事实存储在数据库中。为简化起见，假设我们要讨论的对象仅为以名字标识的人。我们可以按如下方式陈述事实：

*   Alan 是 Betty 的兄弟。
*   Charles 是 Betty 的兄弟。
*   Betty 是 Fred 的父母。

你可以看到这些事实，并轻易推断出 Alan 和 Charles 都是 Fred 的叔叔。在此过程中，你使用了对“叔叔”一词的理解。如果我们希望计算机系统能做出类似推断，需要为其提供一条表达这种理解的规则。例如：

```
给定任意 X, Y，若存在某个 Z 使得 X 是 Z 的兄弟且 Z 是 Y 的父母，则 X 是 Y 的叔叔。
```

这可简写为：

```
X 是 Y 的叔叔，若 X 是 Z 的兄弟且 Z 是 Y 的父母。
```

此规则是*霍恩子句*的一个例子。子句左侧“**if**”的头部可从右侧所述条件推导得出。霍恩子句用于 Prolog 和 Datalog 等语言，使许多推导规则能简洁地陈述。在对象角色建模（ORM）中，此类规则使用更易读的语法指定，例如：

*   ```
    对于每个 Person1 和 Person2，
    ```

*   ```
              若 Person1 是某个 Person3 的兄弟
    ```

*                                                                   **who** 是 Person[2] 的父母，则 Person1 是 Person2 的叔叔。

为了理解 CIP 的工作原理，让我们看一个示例。该符号基于一种称为 FORML（形式化 ORM 语言）的文本 ORM 语言。图形版本将在后续章节解释。为简化起见，省略了一些约束。UoD 结构在所示概念模式中陈述。

*   ```
    引用方案：                Person(.Firstname); Country(.Code); Year(CE:)
    ```

*   ```
    基础事实类型：             F1        Person lives in Country.
    ```

*   ```
                                                                      F2        Person was born in Year.
    ```

*   ```
                                                                      F3        Person is a brother of Person.
    ```

*   ```
                                                                      F4        Person is a parent of/is a child of Person. Roles: parent, child.
    ```

*   ```
    约束：                        C1        Each Person lives in some Country.
    ```

*   ```
                                                                      C2        Each Person lives in at most one Country.
    ```

*   ```
                                                                      C3        Each Person was born in at most one Year.
    ```

*   ```
                                                                      C4        No Person is a brother of itself.
    ```

*   ```
                                                                      C5        No Person is a parent of itself.
    ```

*   ```
    推导规则：       D1        Person1 is an uncle of Person2 if
    ```

*   ```
                                                        Person1 is a brother of some Person3 who is a parent of Person2.
    ```

*   ```
                                                                      D2        nrChildren of Person = count each child of that Person.
    ```

*引用方案*部分声明了感兴趣的*对象*种类及其引用方式。对象要么是实体，要么是值。*实体*是通过以某种方式将*值*（如名字）与之关联来引用的真实或抽象事物。此处有三种*实体类型*：Person、Country 和 Year。在该 UoD 中，人由名字标识（实际中很少见！）。国家由代码标识（如“CU”代表古巴）。年份由 CE（公元）值标识（如第二次世界大战于 1945 CE 结束）。年份是时间段，因此是实体而非值。

*事实类型*部分声明了感兴趣的事实种类。这指明了对象类型如何参与关系。在本书中，英文对象类型名首字母大写，角色名以小写字母开头。由于数据库列具有“birthyear”等属性名，你可能认为将“Person was born in Year”改写为“Person has Birthyear”更好。

然而，假设我们添加事实类型“Person has Deathyear”。Birthyear 与 Deathyear 之间的形式联系现在被隐藏了。将新事实类型表达为“Person died in Year”揭示了与“Person was born in Year”的语义联系，并使出生年份与死亡年份的比较变得有意义（底层域为 Year）。

属性名常用于 ER、UML 和关系模式中表达事实，但这可能不自然（比较“Person has deathyear”与“Person died in Year”），且除非添加“Year”等域名，否则是不完整的。

*约束*部分声明了事实类型上的约束。此处的示例均为*静态*约束（即每个约束对数据库的每个状态均为真）。模式语言中的保留字以粗体显示。约束 C1 意味着数据库中引用的每个人，我们知道他们至少居住在一个国家。C2 表示没人能同时居住在多个国家。C3 表示没人出生于多个年份；注意我们可能不知道他们的出生年份。约束 C4 表示没人是自己的兄弟，C5 表示没人是自己的父母（兄弟关系和父母关系是非自反的）。

*推导规则*部分声明了叔叔关系的逻辑规则和计算任意人子女数量的函数。叔叔规则使用事实类型读法，以关系风格指定。nrChildren 规则使用角色名，以属性风格指定。
