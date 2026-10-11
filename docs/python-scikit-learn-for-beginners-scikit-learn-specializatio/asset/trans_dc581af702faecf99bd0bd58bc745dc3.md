

# 环境搭建与 Python 快速入门

各种编程语言都提供了可用于机器学习和数据科学任务的库。然而，你将使用 Scikit-Learn 库，它是用 Python 编程语言编写的。Python 灵活且是一门适合初学者的易学语言。在本章中，你将了解如何设置 Python 环境，以便结合 Scikit-learn 运行机器学习和数据科学算法。本章还包含一个面向 Python 绝对初学者的速成课程。本章以一个简单的练习结束。

## 2.1. 环境搭建

### 2.1.1 Windows 搭建

是时候使用 IDE 在 Windows 上安装 Python 了。事实上，我们将在全书中使用 Anaconda，从安装 Python 到在后续章节中编写多线程代码。现在，让我们开始安装吧。本节解释如何在 Windows 上下载并安装 Anaconda。请按照以下步骤下载并安装 Anaconda。

1.  在浏览器中打开以下 URL。
    `https://www.anaconda.com/distribution/`

2.  浏览器将带你进入以下网页。选择最新版本的 Python（撰写本书时为 3.7）。现在，点击 Download 按钮下载可执行文件。根据你的网速，文件将在 2–3 分钟内下载完成。

    ![](Image00006.jpg)

3.  下载完成后运行可执行文件。你很可能会在下载文件夹中找到下载的文件。文件名应类似于 `Anaconda3-5.1.0-Windows-x86_64`。运行文件时将打开安装向导，如下图所示。点击 Next 按钮。

    ![](Image00007.jpg)

4.  现在在许可协议对话框中点击 I Agree，如下截图所示。

    ![](Image00008.jpg)

5.  在选择安装类型对话框中勾选 Just Me 单选按钮。点击 Next 按钮继续。

    ![](Image00009.jpg)

6.  现在将显示选择安装位置对话框。如果需要可更改目录，但建议使用默认设置。安装文件夹至少应有 3 GB 的可用空间供 Anaconda 使用。点击 Next 按钮。

    ![](Image00010.jpg)

7.  在高级安装选项对话框中选择第二项，Register Anaconda as my default Python 3.7。
    点击 Install 按钮开始安装，这可能需要一些时间才能完成。

    ![](Image00011.jpg)

8.  安装完成后点击 Next。

    ![](Image00012.jpg)

9.  在 Microsoft Visual Studio Code 安装对话框中点击 Skip。

    ![](Image00013.jpg)

10. 你已成功在 Windows 上安装 Anaconda。干得漂亮。下一步是取消对话框中两个复选框的勾选。现在，点击 Finish 按钮。

    ![](Image00014.jpg)

### 2.1.2 Mac 搭建

Anaconda 在 Mac 上的安装过程几乎相同。图形界面可能有所不同，但你将遵循与 Windows 相同的步骤。唯一的区别是你必须下载与 Mac 操作系统兼容的可执行文件。本节解释如何在 Mac 上下载并安装 Anaconda。请按照以下步骤下载并安装 Anaconda。

1.  在浏览器中打开以下 URL。
    `https://www.anaconda.com/distribution/`

2.  浏览器将带你进入以下网页。选择适用于 Mac 的最新版本 Python（撰写本书时为 3.7）。现在，点击 Download 按钮下载可执行文件。根据你的网速，文件将在 2–3 分钟内下载完成。

    ![](Image00015.jpg)

3.  下载完成后运行可执行文件。你很可能会在下载文件夹中找到下载的文件。文件名应类似于 `Anaconda3-5.1.0-Windows-x86_64`。运行文件时将打开安装向导，如下图所示。点击 Continue 按钮。

    ![](Image00016.jpg)

4.  现在在 Welcome to Anaconda 3 Installer 窗口中点击 Continue，如下截图所示。

    ![](Image00017.jpg)

5.  重要信息对话框将弹出。直接点击 Continue 以采用默认版本 Anaconda 3。

    ![](Image00018.jpg)

6.  在软件许可协议对话框中点击 Continue。

    ![](Image00019.jpg)

7.  必须阅读许可协议并点击 Agree 按钮，然后才能再次点击 Continue 按钮。

    ![](Image00020.jpg)

8.  在出现的下一个窗口中直接点击 Install。

    ![](Image00021.jpg)

    系统将提示你输入密码。使用你登录 Mac 电脑时的相同密码。现在，点击 Install Software。

    ![](Image00022.jpg)

9.  在下一个窗口中点击 Continue。此时你也可以选择安装 Microsoft VSCode。

    ![](Image00023.jpg)

    下一个屏幕将显示安装成功完成的消息。点击 Close 按钮关闭安装程序。

    ![](Image00024.jpg)

    就这些。你已成功在 Mac 电脑上安装 Anaconda。现在，你可以在 Jupyter 和 Spyder 中编写 Python 代码，就像在 Windows 中一样。

### 2.1.3 Linux 搭建

我们已为 Windows 和 Mac 使用了 Python 的图形安装程序。然而，我们将使用命令行在 Ubuntu 或 Linux 上安装 Python。Linux 也更节省资源，且软件安装特别容易。请按照以下步骤在 Linux（Ubuntu 发行版）上安装 Anaconda。

1.  前往以下链接，从最新可用版本复制安装程序 bash 脚本。
    `https://www.anaconda.com/distribution/`

    ![](Image00025.jpg)

2.  第二步是下载安装程序 bash 脚本。登录到你的 Linux 计算机并打开终端。现在，进入 `/temp` 目录并使用 `curl` 下载你从 Anaconda 主页获取的 bash 脚本。

    ```
    $ cd /tmp
    $ curl -o https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh
    ```

3.  你还应通过 SHA-256 校验和使用加密哈希验证来验证安装程序的完整性。

    ```
    $ sha256sum Anaconda3-5.2.0-Linux-x86_64.sh
    ```

    你将获得以下输出。

    ```
    09f53738b0cd3bb96f5b1bac488e5528df9906be2480fe61df40e0e0d19e3d48  Anaconda3-5.2.0-Linux-x86_64.sh
    ```

4.  第四步是运行 Anaconda 脚本，如下图所示。

    ```
    $ bash Anaconda3-5.2.0-Linux-x86_64.sh
    ```

    命令行将产生以下输出。系统将要求你查看许可协议。持续按 Enter 键直到到达末尾。

    ```
    Output
    Welcome to Anaconda3 5.2.0
    In order to continue the installation process, please review the license agreement.
    Please, press Enter to continue
    >>>
    ...
    Do you approve the license terms? [yes|No]
    ```

    当你到达许可协议底部时输入 `Yes`。

5.  同意许可协议后，安装程序将要求你选择安装位置。
    直接按 Enter 选择默认位置。如果需要，也可以指定其他位置。

    ```
    Output
    Anaconda3 will now be installed on this location: /home/tola/anaconda3
    - Press ENTER to confirm the location
    - Press CTRL-C to abort the installation
    - Or specify a different location below
    [/home/tola/anaconda3] >>>
    ```

    按下 Enter 后安装将继续。再次提醒，请耐心等待，因为安装过程需要一些时间才能完成。

6.  安装完成后你将收到以下结果。如果你想使用 `conda` 命令，请输入 `Yes`。

