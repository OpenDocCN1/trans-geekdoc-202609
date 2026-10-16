
在这些情况下，并没有为编译器指定任何信息来写入文件。如果你查看系统中的任何文件（例如），你会看到 Microsoft Corporation 作为版权所有者。你还会得到程序的相关信息，可能包括这些信息。这并不意味着恶意软件作者会在文件中写入他们的名称。事实上，你可能会在这里发现虚假信息。软件供应商可以做的一件事是对可执行文件进行签名。这意味着添加一个加密签名。大型供应商，尤其是 Microsoft，会对可执行文件进行签名。即使恶意软件作者在元数据中插入信息，假装文件来自 Microsoft，可执行文件也不会拥有正确的加密签名。你应该能够看到签名不是使用合法 Microsoft 证书生成的。

#### VirusTotal

另一种在不执行程序的情况下进行静态分析的方法是获取样本的哈希值。可以使用多种哈希算法。常见的一个是消息摘要 5（MD5）。这是一种已有数十年历史的哈希算法，广为人知，虽然在某些应用中它并不是最佳选择，因为它可能易受碰撞影响（即两个不同的数据集生成相同的值），但对于恶意软件分析来说，获得文件哈希通常不被认为是问题所在。在下面的示例中，你可以看到在 Windows 系统上运行哈希算法以获得 MD5 值。

**获取 MD5 哈希值**

```
C:\Users\kilroy\Documents
md5sum.exe bogus.exe
846693bf0c4c678e9727cfade75ebce3 *bogus.exe

C:\Users\kilroy\Documents
```

当然，你也可以使用其他哈希算法，例如安全哈希算法（SHA）。SHA‑1 的哈希值比 MD5 更长，这意味着哈希空间更大。SHA‑1 正逐渐被 SHA‑256 取代，后者的哈希空间显著更大。与 SHA‑1 相比，SHA‑256 的碰撞概率显著更低，也远低于 MD5。一旦你拥有哈希值，就可以使用它来检查恶意软件数据库，这些数据库通常存储哈希值以供比对。防病毒程序一般会将哈希值与已知恶意软件进行匹配。

有一个网站可以让你将恶意软件与多个防病毒程序进行比对。VirusTotal 目前会检查数十个防病毒程序。如果你有一个文件，可以上传它，VirusTotal 会通过获取哈希值并将其与数十个防病毒程序的数据库进行比对。[Figure 8.9](#c08.xhtml#c08-fig-0009) 显示了对位于我的垃圾邮件文件夹中的 PDF 进行测试的结果，这看起来像是一次钓鱼尝试。

![FIGURE 8.9 VirusTotal results](images/c08f009.png)

[**FIGURE 8.9**](#c08.xhtml#R_c08-fig-0009) VirusTotal results

[Figure 8.9](#c08.xhtml#c08-fig-0009) 展示了不同防病毒程序如何识别该样本。在数十个防病毒程序中，有九个将该样本标记为恶意软件，其余均将其标记为干净。这仅说明了防病毒程序的看法，并不提供任何细节。如果我们进入“Details”标签，将获得来自不同加密算法的哈希值。[Figure 8.10](#c08.xhtml#c08-fig-0010) 展示了文件的其他属性，包括多个哈希值、文件类型以及该文件首次提交到 VirusTotal 的时间。

![FIGURE 8.10 VirusTotal details](images/c08f010.png)

[**FIGURE 8.10**](#c08.xhtml#R_c08-fig-0010) VirusTotal details

除了这些数据外，“Details”标签还包含关于 PDF 文件被滥用的常见属性以及样本中出现的实例数量的详�>"�<unk><unk><unk><unk><unk><unk><unk><unk> 以及在样本中出现的 EXIF 文件元数据的信息。通过 VirusTotal，<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>: 1000
