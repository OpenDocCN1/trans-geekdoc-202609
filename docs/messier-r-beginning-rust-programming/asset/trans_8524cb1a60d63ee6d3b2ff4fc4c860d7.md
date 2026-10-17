
Back Orifice 是由一位使用化名 Sir Dystic 的程序员，与 Cult of the Dead Cow (cDc) 合作编写的，目的是实现远程系统管理。那时远程管理 Windows 系统的方法并不多，因此 Back Orifice 既可以用于合法目的，也可以用于不合法目的，包括在用户不知情的情况下远程控制任何计算机。它采用客户端/服务器架构：在目标系统或（理想情况下）自己的 Windows 服务器上安装一个小型服务器程序，然后使用客户端连接到服务器并发送命令。

在 Back Orifice（BO）和 Back Orifice 2000（BO2K）中，客户端是图形用户界面（GUI）。我们将保持简化，只关注客户端/服务器的通信部分，并让用户通过命令行与服务器交互。名称 Back Orifice 其实是个玩笑：当时 Microsoft 有一款叫 BackOffice Server 的产品，将多个常用服务器应用打包在一起，后来演变为 Small Business Server。因此，如果我们要管理 Windows 系统，使用 Back Orifice 服务器是合理的选择。当然，*back orifice* 也暗指 *backdoor*，而 BO 正好提供了这一点。

本练习的目的是展示客户端/服务器的活动。更具体地说，它旨在让你了解网络编程的两个方面——发送端和接收端，因为根据不同的角色，开发过程会有所不同。在接收端，我们需要设置监听器，这比仅仅建立输入/输出通道并写入以发送消息到另一系统要复杂得多。

单纯往返发送和接收流量本身并不有趣，我们希望传输的内容要有实质或意义。这里的做法是：向远程系统发送命令，接收该命令的响应，然后将响应回传给发送系统。这些命令大致是操作系统命令，但我们会让它们尽可能系统无关，只要远程服务器运行我们编写的服务器即可，与其具体是什么无关。

编程中常见的问题之一是输入未经验证，尤其是在 Web 编程中。我们不会直接接受任意命令并直接传递给操作系统，而是确保只接受我们理解并批准的命令。另一个问题是程序员有时会假设从程序其他部分获得的数据是“干净”的。如果我们很懒，可能会假设从客户端得到的输入已经被验证过，但这并不妨碍有人恶意发送无效命令。因此，我们将在客户端和服务器两端都进行验证。

理想情况下我们会在客户端和服务器之间使用加密，但为了保持简洁，让你能够仅从网络编程的角度观察过程，我们暂时不使用加密。本章仅讨论服务器的实现，客户端的实现将在下一章中处理。

**PLANNING**

由于我们需要两个相互通信的程序，这增加了复杂度。一旦开始变得复杂，绘制程序的大致功能图就非常有帮助。文档虽然不需要像数十页的完整设计文档那样详尽，但对任何有实质的程序以及将来可能由他人维护或扩展的程序来说，文档都是必不可少的。

常见的规划方法是先写下（在纸上、文本文档或带有格式和各种功能的 Office 类文档中）程序的需求。我们的需求相对简单，可以列出以下几点：

**客户端**

*   [Take input from user](#)  
* [Assess input for valid command](#)  
* [Initiate communication channel with server](#)  
* [Send communication](#)  
* [Receive response](#)  
* [Print out response for user](#)  
* [Lather, rinse, repeat](#)

**服务器**

* [Start listener](#)  
* [Wait for input from client](#)  
* [Receive input](#)  
* [Validate command](#)  
* [Send command to operating system](#)  
* [Receive response from operating system](#)  
* [Transmit response to client](#)  
* [Return to waiting for input from client](#)

这些需求呈现出一种流程，几乎可以直接绘制成流程图，直观展示程序的运行方式。从中我们可以得到很多有用的信息：首先，我们需要能够获取用户输入，具体方式不限——可以是命令行参数，也可以是交互式提示。我们还需要服务器能够监听网络端口，供客户端连接。

另一种文档方式是使用可视语言，例如通用建模语言（UML）。UML 用于直观地展示系统或软件的设计，复杂系统的图形往往比纯文本更易理解。虽然图表无法展示所有细节，但配合文字说明可以更清晰地传达功能。我们将创建一个活动图（activity diagram），展示程序的整体流程。如 [Figure 6.1](#c06.xhtml#c06-fig-0001) 所示，该图描绘了客户端程序的流程，包括一个决策点。由于我们假设用户希望连续发送多条命令，因此需要提供一种方式让用户表示“完成”并退出程序。我们可以强制用户按 Ctrl-C 终止程序，但这并不优雅，也不符合良好编程实践。

![FIGURE 6.1: UML diagram of the client program](images/c06f001.png)

[**FIGURE 6.1**](#c06.xhtml#R_c06-fig-0001): UML diagram of the client program
