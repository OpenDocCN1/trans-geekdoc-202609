

3. 点击 `Submit & Search` 以搜索 Hashes.com 数据库。几秒钟后，你应该会看到一份已破解密码列表：

```
64f12cddaa88057e06a81b54e73b949b:Password1
85f4aaf6ac4fac1d9b55e6b880bcda3e:CaptainMarvel
920ae267e048417fcfe00f49ecbd4b33:P@$$w0rd!
d6566eae841e523df8fd96a42bcbd4ac:superman20
fc525c9683e8fe067095ba2ddc971889:Passw0rd!--snip--
```

![Figure 7-2: Hashes.com takes your NTLM hashes as input and outputs any cracked passwords it finds in its database.](image_fi/502000c07/f07002.png)

Figure 7-2: Hashes.com takes your NTLM hashes as input and outputs any cracked passwords it finds in its database.

Hashes.com 找到了五个密码！由于它不断向数据库中添加新密码，因此可能能够破解本书中我们将使用的更多简单密码。

我们能够使用免费的在线查找工具从 Windows 虚拟机中恢复至少五个密码——攻击者可能只需要 `one` 个用户名和密码，就能入侵网络、公司或政府机构。这就是为什么组织中的 `every user` 都选择更长、更难猜测的密码非常重要。

### John the Ripper

John the Ripper，通常缩写为 JtR 或简称 John，是最古老的密码破解工具之一；自第一个版本的 John 发布以来，已有 20 多年的历史。John 包含在 Kali Linux 的 Kali 菜单按钮的 `05 - Password Attacks` 菜单下。

John 从命令行终端运行，但还有一个名为 Johnny 的 John 版本，带有图形用户界面 (GUI)，更易于使用。Johnny 未包含在最新版本的 Kali 中。要安装它，请打开一个新终端窗口并输入以下两个命令：

```
kali@kali:~$ sudo apt update
kali@kali:~$ sudo apt install johnny
```

在第一个命令后，你可能需要输入密码（`kali`）。安装后，Johnny 通常会出现在 John 下方的 `05 - Password Attacks` 菜单中，但你也可以通过在终端输入 `johnny` 来运行它。

我们将在 Johnny 中使用两种方法来破解更多被盗的 Windows 密码。我们将尝试字典攻击来破解常见密码，并尝试掩码攻击来破解带有变体的密码。你在 Johnny 中所做的一切，也都可以在终端中使用 John 完成；使用 Johnny 后，你可以查找 John 的命令并尝试它们，以了解整个过程。

#### A Dictionary Attack

我们将从尝试字典攻击开始。也称为 `wordlist attack`，`dictionary attack` 是针对我们试图破解的哈希值测试一系列单词。John the Ripper 将对我们提供的长列表中常见密码的每个密码进行哈希处理，并将每个哈希值与我们的 Windows 哈希值进行比较。如果找到匹配项，我们就破解了该密码。

Kali 内置了几个单词列表，包括 RockYou 单词列表。RockYou 是一家公司，在 2009 年涉及保护不力的 Web 应用程序的著名泄露事件中丢失了 3200 万用户的密码。RockYou 暴露的明文密码列表仍然是检查密码安全性的最佳免费单词列表之一。

1. 要访问 RockYou 单词列表，请在终端窗口中输入以下命令：

```
kali@kali:~$ sudo gunzip /usr/share/wordlists/rockyou.txt.gz
```

此命令将单词列表提取为 `/usr/share/wordlists` 文件夹中的 `rockyou.txt`，以便可以在 John 和 Johnny 中将其用作字典。

2. 通过单击 Kali 菜单按钮并选择 `05 - Password Attacks`▶`johnny` 打开 Johnny。

3. 单击 `Open password file`▶`Open password file (PASSWD format)`。找到我们先前创建的 `Windows_hashes.txt` 文件，如 [Figure 7-3](#c07.xhtml#figure7-3) 所示，并选择它以加载密码哈希文件。

![Figure 7-3: Opening the `Windows_hashes.txt` password file in Johnny](image_fi/502000c07/f07003.png)

Figure 7-3: Opening the `Windows_hashes.txt` password file in Johnny

4. 在 Johnny 左侧单击 `Options`，然后在 Options 窗口中单击 Attack mode 下的 `Wordlist` 选项卡。在 Wordlist file: 文本框中输入 `/usr/share/wordlists/rockyou.txt`，如 [Figure 7-4](#c07.xhtml#figure7-4) 所示。

![Figure 7-4: Loading the `rockyou.txt` wordlist through Johnny](image_fi/502000c07/f07004.png)

Figure 7-4: Loading the `rockyou.txt` wordlist through Johnny

5. 仍在 Options 窗口中，在 Session details 下，从 Current hash format: 下拉列表中选择 `NT`，如 [Figure 7-5](#c07.xhtml#figure7-5) 所示。这告诉 Johnny 密码哈希处于 NTLM 格式。

![Figure 7-5: Choosing `NT` as the input password hash format](image_fi/502000c07/f07005.png)

Figure 7-5: Choosing `NT` as the input password hash format

6. 在左侧单击 `Passwords`，然后单击顶部的 `Start new attack`。

几乎立即，Johnny 将显示几个已破解的密码，如 [Figure 7-6](#c07.xhtml#figure7-6) 所示。（如果看不到任何密码，请确保在第 5 步中将当前哈希格式更改为 NT。）

![Figure 7-6: It takes Johnny almost no time to crack five or six passwords using the hashes we captured.](image_fi/502000c07/f07006.png)

Figure 7-6: It takes Johnny almost no time to crack five or six passwords using the hashes we captured.

我们花了几分钟来捕获密码哈希，但使用 RockYou 单词列表进行字典攻击破解前五六个密码只需不到一秒钟。如果你使用只有几个数字和符号的简单一词或两词密码，恶意黑客只需做这些工作就能拿到你的密码。

RockYou 单词列表包含了我们为用户设置的几个密码。其他密码足够复杂，未出现在列表中。让我们看看如何使用 Johnny 中的另一个选项——掩码攻击——来破解一两个更多密码。

#### A Mask Attack

`mask attack` 从部分信息开始，例如旧密码，并添加字符以尝试破解类似密码。你或你认识的人很有可能正在通过在末尾添加数字或符号来重复使用旧密码，例如 `badpassword20!`。这种行为比你想象的更常见，并使许多密码容易受到掩码攻击。

如果攻击者获得某人密码片段，掩码攻击也很有效。想象一下 Kara，我们的一名 Windows 用户，在 CatCo Worldwide Media 找到了一份工作。当路过 Kara 的办公桌时，一个爱管闲事的同事看到 Kara 扔进垃圾桶的一张便利贴。它撕破了，但看起来上面可能写着密码的一部分：`SuperGir`（参见 [Figure 7-7](#c07.xhtml#figure7-7)）。

社会工程师称这种行为为 `dumpster diving`——字面意思就是翻找他人的垃圾以寻找有用信息，例如银行对账单、信用卡优惠，或写在信封背面或像这样便利贴上的密码。

![Figure 7-7: Kara’s torn sticky note with what looks like part of her password](image_fi/502000c07/f07007.png)

Figure 7-7: Kara’s torn sticky note with what looks like part of her password

在 Johnny 中，我们可以在 `SuperGir` 末尾添加通配符字符，以尝试猜测 Kara 密码的其余部分可能是什么。`wildcard` 是一个占位符，可以被一组字母、数字或符号中的任何一个替换。我们可以使用通配符字符 `?u` 表示大写字母，`?l` 表示小写字母，`?d` 表示数字（0–9），`?s` 表示特殊符号，或 `?a` 表示所有可打印字符（字母、数字、标点符号和特殊字符）。

