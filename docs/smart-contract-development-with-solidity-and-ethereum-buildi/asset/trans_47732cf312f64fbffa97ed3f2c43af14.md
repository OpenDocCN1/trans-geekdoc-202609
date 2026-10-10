
16. 此外，通过点击您选择的 VM，您可以监控其每小时/每日的使用统计信息，如下截图所示：

     ![](images/Figure_3.1.17.jpg)

     **Figure 3.1.17**

看看仅通过几次简单的点击就在 Azure 上设置 VM 是多么容易。现在您不必依赖任何物理机器来完成您的工作。

# [工具和包的分步安装](#toc.xhtml#s51a)

正如我在前面章节所述，让我们开始其他工具和包的分步安装：

1.  **安装 Chrome 浏览器** - 第一步是安装 Chrome 浏览器。如果您已经安装了 Chrome 浏览器，请打开浏览器并参考步骤 3，否则请下载 Chrome 浏览器：

    ![](images/Figure_3.1.18.jpg)

    **Figure 3.1.18**

2.  阅读 `Google` 条款和服务，并将其安装在刚创建的新机器上。

    ![](images/Figure_3.1.19.jpg)

    **Figure 3.1.19**

3.  现在我们必须安装 `MetaMask`，这是一个 Chrome 插件，将帮助我们进行身份验证和测试。`MetaMask` 是一个工具，可帮助您在浏览器中快速与以太坊网络交互。它使用 `infura.io`。请注意 `Metamask` 不支持挖矿和合约部署。

     从 GitHub 以下 URL 下载 `MetaMask`：`[https://github.com/MetaMask](https://github.com/MetaMask)`。如下截图所示，选择 `Pinned repositories` 中显示的 `metamask`-extension 链接并点击它：

    ![](images/Figure_3.1.20.jpg)

    **Figure 3.1.20**

4.  我选择了 `4.7.4` 版本；当您尝试下载时，可能会看到最新的稳定版本。通过点击链接 `metamask-chrome-4.7.4.zip` 下载 Chrome 插件，如下截图所示：

    ![](images/Figure_3.1.21.jpg)

    **Figure 3.1.21**

5.  将下载的 zip 文件解压到 Windows 上的任意位置：

    ![](images/Figure_3.1.22.jpg)

    **Figure 3.1.22**

6.  现在在 Chrome 中输入以下 URL 打开 Chrome 扩展设置：`chrome://extensions`。开启 `Developer mode`，如下截图所示，然后点击 `LOAD UNPACKED` 以加载解压后的下载扩展：

    ![](images/Figure_3.1.23.jpg)

    **Figure 3.1.23**

7.  现在导航到 `MetaMask` Chrome 扩展解压的文件夹并选择该根文件夹，如下截图所示：

    ![](images/Figure_3.1.24.jpg)

    **Figure 3.1.24**

8.  点击 `OK` 后，扩展将加载到 Chrome 中，您将看到 `MetaMask` 主页，确认该扩展现在是 Chrome 浏览器的一部分。您将在 Chrome 右上角看到一个狐狸图标作为扩展。现在您可以返回之前打开的 Chrome 扩展页面，并禁用我们在加载解压扩展时启用的 `Developer mode`：

    ![](images/Figure_3.1.25.jpg)

    **Figure 3.1.25**

9.  现在下载 `Visual Studio Code`，这是一个帮助我们进行开发的 IDE。`VS Code` 广受欢迎，是微软提供的轻量级免费 IDE。导航至 URL：`[https://code.visualstudio.com/](https://code.visualstudio.com/)`。下载最新稳定版本，如下截图所示：

    ![](images/Figure_3.1.26.jpg)

    **Figure 3.1.26**

10. 下载可执行文件后，点击它进行安装。阅读许可协议并接受，按照安装向导的说明将 `VS Code` 安装到您的机器上：

     ![](images/Figure_3.1.27.jpg)

     **Figure 3.1.27**

11. 现在轮到下载 `NPM`。导航至 URL - `[https://nodejs.org/en](https://nodejs.org/en)` 并下载窗口上显示的最新发布稳定版本。我正在下载 `8.11.2 LTS` 版本的 `NPM`，如下截图所示：

     ![](images/Figure_3.1.28.jpg)

     **Figure 3.1.28**

12. 下载安装程序后点击它并按照步骤操作。

     ![](images/Figure_3.1.29.jpg)

     **Figure 3.1.29**

13. 保持所有设置为默认值，点击 `Next` 按钮直到安装成功完成：

     ![](images/Figure_3.1.30.jpg)

     **Figure 3.1.30**

14. 安装完成后点击 `Finish` 按钮：

     ![](images/Figure_3.1.31.jpg)

     **Figure 3.1.31**

15. 现在，正如本节前面所述，我们还需要一个包管理器。让我们也安装它，即 `Chocolatey`。它可以使用 `PowerShell` 命令安装，我们可以在 URL `[https://chocolatey.org/](https://chocolatey.org/)` 上获取命令/脚本。访问网站并点击 `Install Chocolatey Now` 按钮，如下截图所示：

     ![](images/Figure_3.1.32.jpg)

     **Figure 3.1.32**

16. 在跳转的页面上，向下滚动到看到子标题 `Install with PowerShell.exe` 的部分。复制脚本，如下截图红框所示。脚本内容为：

     ```
     Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
     ```

     ![](images/Figure_3.1.33.jpg)

     **Figure 3.1.33**

17. 现在从 Windows 开始菜单打开 PowerShell 窗口，如下所示，点击 `Run as administrator` 启动 PowerShell 命令提示符：

     ![](images/Figure_3.1.34.jpg)

     **Figure 3.1.34**

18. 命令提示符将如下截图所示：

     ![](images/Figure_3.1.35.jpg)

     **Figure 3.1.35**

19. 现在将复制的脚本粘贴到命令提示符中并按 `Enter`。

     ![](images/Figure_3.1.36.jpg)

     **Figure 3.1.36**

20. 一旦 `Chocolatey` 命令和 `NuGet` 包就位，我们将使用 `Chocolatey` 的 install 命令安装 GitHub 客户端；这将安装开发过程中使用的其他有用工具。

     因此，在命令提示符中输入命令：`choco install git -params "/GitAndUnixToolsOnPath"`，如下截图所示，然后按 `Enter`。

     ![](images/Figure_3.1.37.jpg)

     **Figure 3.1.37**

21. 命令提示符上的安装程序将询问是否运行脚本以允许全局配置。您可以输入 `Y` 表示是，然后按 `Enter` 以允许。

     ![](images/Figure_3.1.38.jpg)

     **Figure 3.1.38**

22. 现在关闭并重新打开 PowerShell 窗口，以确保所有内容均已正确安装。

     ![](images/Figure_3.1.39.jpg)

     **Figure 3.1.39**

23. 现在让我们执行以下命令：

     *   关闭 Git 中的所有安全调用验证功能：`git config --system http.sslverify false`

         ![](images/Figure_3.1.40.jpg)

         **Figure 3.1.40**

     *   通过 `NPM` 安装 node 插件构建工具：`npm install -g node-gyp`

         ![](images/Figure_3.1.41.jpg)

         **Figure 3.1.41**

     *   安装 Windows 构建工具：`npm install --global --production windows-build-tools`

         ![](images/Figure_3.1.42.jpg)

         **Figure 3.1.42**

     *   安装 Windows 构建工具将花费一些时间，请耐心等待，在此期间如果您愿意可以吃点东西 😊。

         ![](images/Figure_3.1.43.jpg)

         **Figure 3.1.43**

24. 安装 `Test RPC`，即用于测试我们解决方案的本地以太坊服务器：`npm install -g ethereumjs-testrpc`

     ![](images/Figure_3.1.44.jpg)

     **Figure 3.1.44**

25. 最后，安装 `Truffle` 工具集：`npm install -g truffle`

     ![](images/Figure_3.1.45.jpg)

     **Figure 3.1.45**

现在我们可以开始开发了，因为我们的工具和软件已就绪，且 Azure 上的开发机器正在运行。是的，设置环境和工具需要大量工作，但请放心，开发和学习这些新工具和技术将会很有趣。

# [结论](#toc.xhtml#s52a)
