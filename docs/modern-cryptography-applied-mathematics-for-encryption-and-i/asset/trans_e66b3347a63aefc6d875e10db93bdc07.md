
-   [密码池的内容永远不会直接导出（即使 VeraCrypt 命令 RNG 生成并导出一个值）]，因此，即使攻击者获得 RNG 生成的值，也无法在会话期间确定或预测（利用该值）RNG 期间生成的其他值（无法从 RNG 生成的值中确定密码池的内容）。<sup>[1](#part0031.xhtml#ch20note1a)</sup>

-   该详细描述为您提供了足够的信息，以评估 PRNG 是否足够随机以满足您的安全需求。VeraCrypt 提供的在线文档包含更详细的信息。

##### Windows EFS

-   鉴于 Windows 是最常用的操作系统，有必要检查加密文件系统（EFS），它于 Windows 2000 introduced。当时它在所有 Windows 版本中均可用。自 Windows XP 起，EFS 仅在 Windows Professional 或更高版本中可用。

-   EFS 的原始（Windows 2000）过程由 Howard Wright 在 SANS Institute 研究文档中描述：

    >   第一次加密文件时，EFS 为账户分配公钥/私钥对。如果可用证书服务，它将生成密钥对。对于独立系统，EFS 将生成自签名证书。加密文件时，EFS 会生成一个称为文件加密密钥（FEK）的随机数。FEK 用于使用数据加密标准（DESX）加密文件内容。DESX 是增强版 DES，基本上使用三个不同的密钥对数据进行三次处理。FEK 存储在系统中，并使用 RSA 公钥加密算法对其进行加密。<sup>[2](#part0031.xhtml#ch20note2a)</sup>

-   加密的 FEK 存储在加密文件的 $EFS 交替数据流中。要解密文件，EFS 使用与加密文件对应的 EFS 数字证书的私钥，解密存储在 $EFS 流中的对称密钥。过程实际上很简单：

    ```
    1. 右键单击要加密的文件或文件夹，然后选择“属性”打开属性对话框（如 [Figure A-8](#part0031.xhtml#ch20fig08) 所示）。
    ![Images](Images/image00770.jpeg)
    ```

    ```
    2. 单击“高级”按钮，在“高级属性”窗口中，勾选“加密受保护数据”复选框（如 [Figure A-9](#part0031.xhtml#ch20fig09) 所示），然后单击“确定”。
    ![Images](Images/image00771.jpeg)
    ```

**FIGURE A-8    EFS File Properties dialog**

**FIGURE A-9    Encrypting the EFS file**

-   文件名随后在 Windows 资源管理器中显示为绿色。

**Note**

-   重要的是，您必须备份 EFS 密钥。如果不备份，系统崩溃时，您将无法恢复密钥并解密文件，导致加密的数据永久丢失。幸运的是，Microsoft 提供了易于遵循的备份密钥的说明，网址为 [http://windows.microsoft.com/en-us/windows/back-up-efs-certificate#1TC=windows-7](http://windows.microsoft.com/en-us/windows/back-up-efs-certificate#1TC=windows-7)。

##### BitLocker

-   微软在 Windows 7 扩展了 EFS 的概念，并加入了 BitLocker，可加密整个驱动器。它仅在 Windows Professional 版本或更高版本中可用。它使用 CBC 模式的 AES，用户可选择 128 位或 256 位密钥。BitLocker 位于“控制面板”>“系统和安全”下，如 [Figure A-10](#part0031.xhtml#ch20fig10) 所示。

![Images](Images/image00772.jpeg)

**FIGURE A-10    Windows BitLocker**

-   加密驱动器的过程很简单：用户选择“打开 BitLocker”选项，如 [Figure A-11](#part0031.xhtml#ch20fig11) 所示。

![Images](Images/image00773.jpeg)

**FIGURE A-11    Turning on BitLocker**

**Note**

-   与 EFS 类似，备份 BitLocker 密钥并将其存储在安全位置很重要。Microsoft 提供了多种备份密钥的选项，网址为 [https://technet.microsoft.com/en-us/library/dd875529(v=ws.10).aspx](https://technet.microsoft.com/en-us/library/dd875529\(v=ws.10\).aspx)。

##### AxCrypt

-   AxCrypt 仅限 Windows，但它是开源产品，可在 [www.axantum.com](http://www.axantum.com) 下载。它与 EFS 有些相似，但包含 EFS 未提供的功能。例如，AxCrypt 允许用户创建自解密文件，仅凭密码即可解密。AxCrypt 支持使用 AES 128 位进行加密，并使用 SHA1 128 位进行密码散列。

-   AxCrypt 安装后，右键单击任何文件或文件夹，AxCrypt 菜单会显示多个选项，如 [Figure A-12](#part0031.xhtml#ch20fig12) 所示。

![Images](Images/image00774.jpeg)

**FIGURE A-12    AxCrypt menu options**

-   选择“加密”选项后，会提示您输入用于解密文件的密码。该密码必须足够长且复杂，以阻碍猜测或破解，但也要易于记忆。密码对话框如 [Figure A-13](#part0031.xhtml#ch20fig13) 所示。

![Images](Images/image00775.jpeg)

**FIGURE A-13    AxCrypt encryption passphrase dialog**

-   加密文件的扩展名改为 .axx，以表明其已使用 AxCrypt 加密。生成可执行文件的选项与加密文件的方式相同，但会生成一个可发送给他人的可执行文件。接收方只需密码即可解密文件。AxCrypt 可加密整个文件夹以及单个文件。

##### FileVault

-   FileVault 是 Mac OS 附带的加密工具，大致相当于 Microsoft BitLocker。它于 Mac OS X 10.3 首次引入，使用 256 位 AES 密钥加密数据。它易于使用，并在 Apple 在线文档 [https://support.apple.com/en-us/HT204837](https://support.apple.com/en-us/HT204837) 中详细说明。

-   与 BitLocker 类似，用户只需打开 FileVault（如 [Figure A-14](#part0031.xhtml#ch20fig14) 所示），即可加密该用户的文件目录。每个 Macintosh 用户可以选择是否使用 FileVault。虽然 FileVault 不像 BitLocker 那样提供完整的驱动器加密，但它易用，并会加密用户的所有文件，包括敏感文件。

![Images](Images/image00776.jpeg)

**FIGURE A-14    Turning on FileVault**

##### AES Crypt

-   AES Crypt 是免费开源软件，可在 Windows、Linux、Macintosh 以及一些移动设备操作系统上运行。Java 和 C# 库使开发人员能够将 AES Crypt 集成到程序中。AES Crypt 使用 256 位 AES 加密文件。

-   安装 AES Crypt 后，右键单击任何文件，将显示“AES 加密”选项，如 [Figure A-15](#part0031.xhtml#ch20fig15) 所示。

![Images](Images/image00777.jpeg)

**FIGURE A-15    AES Crypt options**

-   选择 AES Crypt 后，会提示您输入文件的密码（如 [Figure A-16](#part0031.xhtml#ch20fig16) 所示）。与其他驱动器/文件加密工具一样，密码的选择很重要，因为它可能是加密安全的薄弱环节。

![Images](Images/image00778.jpeg)

**FIGURE A-16    AES Crypt Password dialog**

-   AES Crypt 有两个问题：它仅加密文件，不加密文件夹；并且会复制文件并对复制件进行加密。您需要删除未加密的原始文件。

#### E-mail Encryption
