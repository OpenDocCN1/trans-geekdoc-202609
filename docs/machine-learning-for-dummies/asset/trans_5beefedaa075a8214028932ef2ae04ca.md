

# 安装 Anaconda

文件名各不相同，但通常在 32 位系统上显示为 `Anaconda3-2020.07-Windows-x86.exe`，在 64 位系统上显示为 `Anaconda3-2020.07-Windows-x86_64.exe`。版本号包含在文件名中。在此情况下，文件名指的是版本 3.2020.07，即本书使用的版本。如果你使用其他版本，可能会在源代码中遇到问题，并在使用时需要进行调整。

## 双击安装文件

你会看到一个欢迎对话框，告知你安装的是 32 位还是 64 位版本的 Anaconda。请确保选择正确的版本。

## 单击 Next

向导会显示许可协议。请务必阅读许可协议，以了解使用条款。

## 单击 I Agree（如果你同意许可协议）

系统会询问你要执行哪种安装类型，如 [Figure 4-1](#c04.xhtml#c04-fig-0001) 所示。在大多数情况下，你希望仅为自己安装该产品。

![FIGURE 4-1: Tell the wizard how to install Anaconda on your system.](images/9781119724018-fg0401.png)

[FIGURE 4-1:](#c04.xhtml#rc04-fig-0001) Tell the wizard how to install Anaconda on your system.

## 选择一种安装类型，然后单击 Next

向导会询问你在磁盘上的哪个位置安装 Anaconda。本书假设你使用默认位置。如果你选择其他位置，可能需要在本书后面修改一些步骤以适应你的设置。

## 选择安装位置（如有必要），然后单击 Next

你会看到高级安装选项，如 [Figure 4-2](#c04.xhtml#c04-fig-0002) 所示。这些选项默认已选中，在大多数情况下没有理由更改它们。本书假设你已使用默认选项设置 Anaconda。

## 更改高级安装选项（如有必要），然后单击 Install

你会看到一个带有进度条的安装对话框。安装过程可能需要几分钟，请喝杯咖啡，看会儿漫画。安装过程结束后，你会看到一个已启用的 Next 按钮。

![FIGURE 4-2: Configure the advanced installation options.](images/9781119724018-fg0402.png)

[FIGURE 4-2:](#c04.xhtml#rc04-fig-0002) Configure the advanced installation options.

## 单击 Next

（如果你看到一个带有 PyCharm 链接的页面，[`https://www.jetbrains.com/pycharm/`](https://www.jetbrains.com/pycharm/)，请再次单击 Next。）向导会告诉你安装已完成。此页面包括 Anaconda 教程和了解更多有关 Anaconda 的选项。如果保持选中状态，你会看到相应页面加载到浏览器中。

## 单击 Finish

你现在可以开始使用 Anaconda 了。

# 下载数据集和示例代码

本书是关于使用 Python 执行机器学习任务。当然，你可以花所有时间从头开始创建示例代码、调试它，然后才发现它与机器学习的关系，或者你可以采取简单的方法，从 [`www.dummies.com`](https://www.dummies.com/) 下载预写代码，以便立即开始工作。同样，创建足够大的数据集用于机器学习目的需要相当长的时间。幸运的是，你可以使用某些数据科学库提供的功能轻松访问标准化的预创建数据集（这些库对于机器学习也同样适用）。以下部分将帮助你下载和使用示例代码和数据集，以便节省时间并立即开始处理数据科学特定任务。

## 使用 Jupyter Notebook

为了使本书中相对复杂的代码更易于处理，你将使用 Jupyter Notebook。此界面让你轻松创建 Python 笔记本文件，其中可以包含任意数量的示例，每个示例都可以单独运行。该程序在浏览器中运行，因此你用于开发的平台无关紧要；只要它有浏览器，你就应该没问题。

### 启动 Jupyter Notebook

你从 Anaconda Navigator 访问 Jupyter Notebook，它还提供对特定环境支持的各种应用程序的集中访问。默认环境或通道，base (root)，直接支持 Python 开发。`ML4D2ER` 文件夹中提供的 `Setup.readme` 文件说明了如何设置单独的 R 通道。[Figure 4-3](#c04.xhtml#c04-fig-0003) 显示了 base (root) 通道的内容。

![Tip](images/tip.png)注意，每个条目都会告诉你将访问哪个版本的产品。对于本书，你使用 Jupyter Notebook 6.0.3。如果你看不到版本 6.0.3，请单击 Jupyter Notebook 条目右上角的齿轮图标，并从菜单中选择 Install Specific Version ⇒ 6.0.3。Anaconda Navigator 将引导你完成正确版本的安装过程。

要启动 Jupyter Notebook，只需在 Jupyter Notebook 条目中单击 Launch。[Figure 4-4](#c04.xhtml#c04-fig-0004) 显示了在 Chrome 浏览器中查看时界面的外观。这是主页，你可以在此处执行诸如创建新文件夹来包含项目等操作。你系统上的精确外观取决于你使用的浏览器和安装的平台类型。

![FIGURE 4-3: Anaconda Navigator provides centralized access to every development need.](images/9781119724018-fg0403.png)

[FIGURE 4-3:](#c04.xhtml#rc04-fig-0003) Anaconda Navigator provides centralized access to every development need.

![FIGURE 4-4: Jupyter Notebook provides an easy method to create machine learning examples.](images/9781119724018-fg0404.png)

[FIGURE 4-4:](#c04.xhtml#rc04-fig-0004) Jupyter Notebook provides an easy method to create machine learning examples.

### 停止 Jupyter Notebook 服务器

无论你如何启动 Jupyter Notebook（或书中其余部分出现的 Notebook），你都需要单击客户端窗口右上角的 Quit 以退出 Notebook。否则，Notebook 服务器将在后台保持运行，你的环境将处于不确定状态，在某些情况下可能导致数据丢失。单击 Quit 后，你会看到一个 Server Stopped 消息框，可以通过单击右上角的 X 将其关闭。关闭浏览器窗口。

如果你已完成使用 Anaconda，请在 Anaconda Navigator 窗口中选择 File ⇒ Quit。在第一次（以及可能随后的）关机过程中，你会看到一个 Quit Application 对话框，必须单击 Yes 以结束 Anaconda Navigator。如果你不想再看到此对话框，可以在单击 Yes 之前选择 Don’t Show Again 将其删除。

![Warning](images/warning.png)有时服务器关机过程比预期的要长。在这种情况下，Anaconda Navigator 会显示一条消息，告诉你它仍在后台工作。在退出之前，请允许它完成需要完成的任何进程。如果你没有正确退出 Jupyter Notebook，也可能会看到此消息。在这种情况下，你需要结束 Anaconda Navigator，因为服务器永远不会停止。

# 定义代码仓库

你在本书中创建和使用的代码将驻留在硬盘上的仓库中。将 *repository* 视为一种文件柜，用于存放代码。Notebook 打开一个抽屉，取出文件夹，并向你显示代码。你可以修改它，在文件夹中运行单个示例，添加新示例，并以自然的方式与代码交互。以下部分将帮助你开始使用 Notebook，以便你了解整个仓库概念的工作原理。

## 定义本书的文件夹

