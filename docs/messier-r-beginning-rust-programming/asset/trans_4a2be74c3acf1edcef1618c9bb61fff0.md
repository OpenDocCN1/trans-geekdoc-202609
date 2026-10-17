
一些人认为 Rust 是一种系统编程语言。系统编程与应用编程的区别在于，应用编程侧重于向最终用户提供有用的功能。系统编程则更多在幕后进行。你可能正在开发一个其他应用程序会消费的服务，或者你正在执行与操作系统低层组件或元素直接交互的低层级任务。有人可能认为系统编程需要使用非常低层级的语言，类似于汇编语言，你直接用处理器能够理解的语言编写，而无需经过编译器将你使用的语言转换为处理器能够理解的语言。

使用汇编语言的原因是它被认为更快，因为编译器可能会在生成的程序中引入低效性。有些人使用 C 语言，以便在程序中更具表达性，同时仍能获得汇编语言所带来的感知优势。C 语言被认为处于汇编语言和像 FORTRAN 这样较高级语言之间（FORTRAN 在 C 发展时是主导语言）。这一信念的问题在于，它假设在汇编语言或 C 中编写代码的程序员是高度熟练的。在汇编语言中编写高度优化代码需要多年的实践——而且是有指导的实践，即不断评估你所写的程序以寻找更好的实现方式。

C 语言的程序员也并无优势。很容易写出质量差的 C 程序，即使是最好的优化编译器也未必能修复糟糕 C 代码的问题。其他语言也如此。在设计良好的语言中写出高质量的程序，可以与在低层次语言中写出质量差的程序同样高效。所谓的“权力”并非一切。我们可以同样在 Rust 中编写系统程序——在速度被视为关键的场景中——并获得 Rust 所提供的所有好处。相反，C 语言的所谓“权力”并未让任何人受益，因为非常少数程序员能够写出既不存在安全漏洞的 C 代码，尤其是在更复杂的程序中。与其拥有一个运行略慢但安全的程序，不如拥有一个因 C 语言弱点而充满漏洞的程序。

当然，事实上，现代处理器速度如此之快，像 Rust 这样更安全、更健壮的语言几乎不会引入用户能察觉的性能差异。性能问题更可能源自输入/输出或图形用户界面，而不是程序本身的运行机制。

因此，我们将使用 Rust 来执行一些低层级工作。我们将探索与各种系统组件的交互，例如获取系统上已连接的磁盘信息。我们也将花一些时间处理 Windows 注册表，因为它是与 Windows 系统交互的重要部分。大量信息存储在 Windows 注册表中，不仅与 Windows 本身相关，还关联到几乎所有已安装的应用程序。

最后，我们将探索 Rust 的其他特性，这些特性可以帮助你在编写程序时更具表达性。你在本书过程中可能一直在思考的一个问题——尤其是如果你来自面向对象背景——是：为什么 Rust 不是面向对象的？或者它真的是面向对象的吗？这取决于你如何定义 *面向对象语言*。Rust 确实包含面向对象语言的某些元素，但也存在面向对象语言的某些部分在 Rust 中不存在或不完全呈现。我们将探讨 Rust 支持的、与面向对象语言相似但并不完全相同的特性。

**WHY BOTHER BANGING ON ABOUT OBJECT-ORIENTED LANGUAGES IN THE CONTEXT OF RUST?** It's easier to understand one thing if you can compare or liken it to something else that is understood. Object-oriented languages have been around for decades now, and a lot of programming today happens in these languages, including Java and C++ as well as others that have object-oriented capabilities but may not be inherently object-oriented in nature, like Python or even PowerShell. These two scripting languages can be used in a procedural manner while also having the capability of having objects written and consumed within any script. They are comfortable going in either direction.

Object-oriented (OO for short) languages come from a desire to separate data from code in a way. Rather than having any code in a program be able to act directly on a piece of data, there is an idea of *encapsulation*, meaning you create a bubble around the data so anything outside the bubble can't get to it directly. Instead, you have a semipermeable membrane using functions (sometimes called methods). To get at the data inside the bubble, you interact with a function that has direct access to the data inside the bubble. You can see a visual representation of this in [Figure 12.1](#c12.xhtml#c12-fig-0001). The functions sit on the edge of the bubble, catching requests and then acting directly on the data inside the bubble. This way, the data stays protected because no one can perform any action on the data anytime they want. The functions created on the edge of the bubble present the actions that are allowed to be taken.

![FIGURE 12.1: Encapsulated data](images/c12f001.png)

[**FIGURE 12.1**](#c12.xhtml#R_c12-fig-0001): Encapsulated data

When you perform this encapsulation of data, you are binding code with the data that the code acts on. You create data that may be represented in any way that makes sense within the bubble, and then you define methods that can be used to interact with the data. The bubble can be made as opaque or transparent as you would like. You may want a complete black box, for instance, where anyone using the data simply has no idea what the data is or how it is represented. They just know what actions they want to perform. This aggregation of data and associated methods is considered an object.

![FIGURE 12.2: Magic card box](images/c12f002.png)

[**FIGURE 12.2**](#c12.xhtml#R_c12-fig-0002): Magic card box

We can look at a specific example. Let's say we have a box of playing cards, as shown in [Figure 12.2](#c12.xhtml#c12-fig-0002). Consider this box our object. We don't know exactly what is inside. We know that if we want a card, we ask the box for a playing card, and it provides one. If we want to reorder the cards, we ask the box to shuffle, and whatever is inside the box is reordered in some new way. You can't see inside the box. The box does all the work for you. Of course, you could open the box (which may mean doing some debugging, for instance, in order to see the internal representation of the cards), but it makes working with the box harder and slows down the process. You can think of an object as a magic box: you ask the box to perform some predefined capability, and the box takes care of it for you without having to trouble you with what is inside the box.
