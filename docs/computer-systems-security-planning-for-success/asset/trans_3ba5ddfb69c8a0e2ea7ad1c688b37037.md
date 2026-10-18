

鉴于密码在包含的常见密码单词列表中，即 `/usr/share/john/password.lst`，你会很快发现 John the Ripper 能够破解 karl 的密码。John the Ripper 也可以遍历所有可能的字符组合进行增量破解，但这需要花费更长时间。为了使这类攻击更加困难，`/etc/shadow` 中的每个哈希值都是基于一个随机数构建的。这个数字被称为 `salt`，并与哈希值一起存储。这意味着，破解工具不能只对单词列表中的每个单词尝试一个哈希值，而必须对单词列表中的每个单词尝试每一种可能的 salt，这会显著减慢速度。现代哈希破解工具可能会使用 [彩虹表](https://en.wikipedia.org/wiki/Rainbow_table)，这样所有可能的哈希值都已预先计算完成。这些表可能会占用数 TB 的磁盘空间，但能让即使是复杂哈希的破解也变得简单得多。

让我们使用名为 `crypt` 的自定义实用程序来证明我们拥有实际密码。该实用程序已安装在你的容器中。我们将先打印出 `/etc/shadow` 中包含 karl 信息的那一行。我们将使用 `grep` 命令将输出限制为包含 `karl` 的内容：

```
root@7f978dd90746:/# cat /etc/shadow | grep karl
karl:$y$j9T$oR2ZofMTuH3dpEGbw6c/y.$TwfvHgCl4sIp0b28YTepJ3YVvl/3UyWKeLCmDV1tAd9:19255:0:99999:7:::
```

shadow 行的第一部分是用户名，即 karl。shadow 行的下一部分，紧跟在第一个冒号之后，是哈希信息。第一组 `$` 之间的字符是所使用的哈希算法版本，在我们的例子中，`y` 表示 yescrypt。第二组 `$` 之间的字符是传递给 yescrypt 的参数，对我们来说始终是 `j9T`。第三组 `$` 之间的字符是你的 salt。最后，第四组 `$` 之间的字符是哈希值。

`crypt` 实用程序调用系统 [`crypt`](https://man7.org/linux/man-pages/man3/crypt.3.html) 命令并打印输出。让我们使用我们破解的密码以及 `/etc/shadow` 中哈希信息的前三部分来运行此实用程序。如果一切顺利，你应该看到与 `/etc/shadow` 中内容匹配的哈希输出：

```
root@7f978dd90746:/# crypt <karl's password> '$y$j9T$oR2ZofMTuH3dpEGbw6c/y.'
$y$j9T$oR2ZofMTuH3dpEGbw6c/y.$TwfvHgCl4sIp0b28YTepJ3YVvl/3UyWKeLCmDV1tAd9
```

1. ① 不要忘记使用你实际破解的密码，并将哈希信息放在单引号中

## 2.12. 复习问题

对称加密和非对称加密有什么区别？分别给出一个常见的应用场景。

什么是哈希，它用于什么？哈希在区块链中是如何使用的？

流密码和分组密码有什么区别？分别给出一个常见的应用场景。

# 3. 恶意软件

## 3.1. 什么是恶意软件？

恶意软件是 `malicious` 和 `software` 这两个词的合成词。该术语用于描述许多不同类型的 `intentionally malicious` 程序。恶意软件与普通糟糕软件之间的关键区别之一在于其创建的意图性。恶意软件旨在损坏或利用计算机系统。它通常会监视、垃圾邮件或以其他方式损坏目标或主机机器。

## 3.2. 恶意软件目标

