
- 如果 Secure Boot 已配置且平台存在 `db` 变量，您会在目录中找到以 `db_` 开头的子文件夹，例如 `db_D719B2CB-3D3A-4596-A3BC-DAD00E67656F`。Chipsec 在转储 `db` 变量时会自动解码其内容，该子文件夹中会出现对应的公钥证书和被授权的 UEFI 映像散列文件。在我们的例子中，共有五个文件——四个证书和一个 SHA256 哈希，如 Figure 17-3 所示。

![image](img/17fig03.jpg)

*Figure 17-3: The contents of a signature database UEFI variable*

这些证书采用 X.509 编码，是定义公钥证书格式的加密标准。我们可以解码这些证书以获取颁发者信息，从而确定哪个签名会通过 Secure Boot 验证。为此，我们使用 openssl 工具包（见“打开 SSL 工具包”方框），从 `https://github.com/openssl/openssl/` 下载并安装工具，然后执行以下命令，将 `certificate_file_path` 替换为本地计算机上存放 openssl 的目录：

```
$ openssl x509 -in certificate_file_path
```

在 Windows 系统上，只需将 X.509 证书文件的扩展名从 bin 改为 crt，然后用资源管理器打开该文件，即可查看解码结果。Table 17-1 列出了我们的结果，包含证书的颁发者和主体。

**Table 17-1:** The Decoded Certificates and Hashes from the UEFI Variable

| **Filename** | **Issued to** | **Issued by** |
| --- | --- | --- |
| *X509-7FACC7B6-127F-4E9C-9C5D-080F98994345-03.bin* | Thinkpad Product CA 2012 | Lenovo Ltd. Root CA 2012 |
| *X509-7FACC7B6-127F-4E9C-9C5D-080F98994345-04.bin* | Lenovo UEFI CA 2014 | Lenovo UEFI CA 2014 |
| *X509-77FA9ABD-0359-4D32-BD60-28F4E78F784B-01.bin* | Microsoft Corporation UEFI CA 2011 | Microsoft Corporation Third-Party Marketplace Root |
| *X509-77FA9ABD-0359-4D32-BD60-28F4E78F784B-02.bin* | Microsoft Windows Production PCA 2011 | Microsoft Root Certificate Authority 2010 |

从表中可以看出，只有 Lenovo 和 Microsoft 签名的 UEFI 镜像才能通过 UEFI Secure Boot 完整性检查。

### THE OPENSSL TOOLKIT

OpenSSL 是一个开源软件库，实现了安全套接层（SSL）和传输层安全（TLS）协议以及通用的密码学原语。它采用 Apache 风格许可证，广泛用于商业和非商业应用。库提供了丰富的 X.509 证书处理功能，无论是解析已有证书还是生成新证书。项目信息可查阅 `https://www.openssl.org/`。

### The dbx Database

与 db 数据库不同，dbx 数据库存储的是公钥证书以及被禁止在启动时执行的 UEFI 可执行文件的哈希值。该数据库也称为 *Revoked Signature Database*，明确列出会导致 Secure Boot 验证失败的镜像，防止包含已知漏洞的模块在平台安全受到威胁时执行。

我们以与 db 签名数据库相同的方式来探索 dbx 数据库的内容。运行 Chipsec 工具后，会生成若干文件夹，其中 `efi_variables.dir` 文件夹应包含一个以 `dbx_D719B2CB-3D3A-4596-A3BC-DAD00E67656f` 开头的子文件夹。该文件夹内存放被禁止的 UEFI 镜像的证书和哈希值。在我们的例子中，该文件夹仅包含 78 条哈希，没有证书，如 Figure 17-4 所示。

![image](img/17fig04.jpg)

*Figure 17-4: Contents of the dbx database (the revoked signature database) UEFI variable*

Figure 17-5 展示了使用 db 和 dbx 数据库进行镜像签名验证的算法。

![image](img/17fig05.jpg)

*Figure 17-5: The UEFI Secure Boot image verification algorithm*

从该图可知，UEFI 可执行文件仅在其哈希值或签名证书在 db 数据库中受信任且不在 dbx 数据库中被列出时才通过验证。否则，Secure Boot 完整性检查将失败。

### Time-Based Authentication

除了 db 和 dbx 数据库，Secure Boot 还使用两个其他数据库，即 dbt 与 dbr。dbr 包含用于验证 OS 恢复加载器签名的公钥证书，这里不作详细讨论。

dbt 包含用于验证 UEFI 可执行文件数字签名时间戳的时间戳证书，从而实现时间基础认证（TBAWS）。正如本章前文所述，TBAWS 通过检查 UEFI 变量的属性来实现。

数字签名有时包含由 *Time Stamping Authority（TSA）* 服务颁发的时间戳。该时间戳反映签名生成的时刻。通过比较签名时间戳与签名密钥的有效期截止时间，Secure Boot 判断签名是在密钥失效之前还是之后生成的。通常，密钥的有效期截止日期是指该密钥被视为受损的时间点。因此，时间戳使得 Secure Boot 能够确认签名是在密钥未被损坏时生成的，从而保证签名的真实性。此机制在 PKI 与 Secure Boot db 证书之间简化了复杂度。

时间基础认证还能避免重新签名相同的 UEFI 镜像。时间戳证明签名在对应密钥失效或撤销之前已完成，因此即使密钥随后失效，签名仍然有效，因为它是在密钥仍然有效且未受损时创建的。

### Secure Boot Keys

现在我们了解了 Secure Boot 如何获取受信任和撤销的公钥证书信息，接下来讨论这些数据库的存储方式以及防止未经授权修改的措施。若攻击者篡改 db 数据库，便可通过插入恶意证书并用对应私钥签名的引导加载程序替换 OS 引导程序，使 Secure Boot 误认为该证书受信任，从而绕过检查。

为防止 db 与 dbx 数据库被未经授权修改，平台或操作系统厂商必须对其数字签名。UEFI 固件在读取这些数据库内容时，首先使用 `Key Exchange Key（KEK）` 公钥验证其数字签名，然后再用 `Platform Key（PK）` 验证每个 KEK。

#### Key Exchange Keys

与 db 与 dbx 数据库类似，公钥列表存放在 NVRAM UEFI 变量中。我们通过之前使用 chipsec 命令生成的结果来查看 KEK 变量的内容。打开结果所在目录，应能看到类似 `KEK_8BE4DF61-93CA-11D2-AA0D-00E098032B8C` 的子文件夹（Figure 17-6），其中包含公钥证书（即 KEK 证书）。

![image](img/17fig06.jpg)

*Figure 17-6: Contents of the KEK UEFI variable*

只有拥有对应私钥的所有者才能修改 db 与 dbx 数据库的内容。本例中仅有 Microsoft 与 Lenovo 两家 KEK 证书，如 Table 17-2 所示。

**Table 17-2:** Certificates in the KEK UEFI Variable

| **Filename** | **Issued to** | **Issued by** |
| --- | --- | --- |
| *X509-7FACC7B6-127F-4E9C-9C5D-080F98994345-00.bin* | Lenovo Ltd. KEK CA 2012 | Lenovo Ltd. KEK CA 2012 |
| *X509-77FA9ABD-0359-4D32-BD60-28F4E78F784B-01.bin* | Microsoft Corporation KEK CA 2011 | Microsoft Corporation Third-Party Marketplace Root |

- 你可以通过导出 KEK 变量并执行我们之前使用的 `openssl` 命令，来发现系统 KEK 证书对应的私钥所有者。

#### Platform Key

- `PK` 是 Secure Boot PKI 密钥层级中的最后一个签名键。正如你可能猜测的，该键用于通过签名 KEK UEFI 变量来验证 KEK。根据 UEFI 规范，每个平台仅有一个 `PK`。通常，该键对应平台制造商。

- 返回在执行 `chipsec` 后创建的 `efi_variables.dir` 的 `PK_8BE4DF61-93CA-11D2-AA0D-00E098032B8C` 子文件夹，在那里你可以找到公共 `PK` 证书的证书。你的证书对应你的平台。因此，既然我们使用了 Lenovo Thinkpad T540p 平台，我们期望我们的 `PK` 证书对应 Lenovo（参见 Figure 17-7）。

![image](img/17fig07.jpg)

*Figure 17-7: The PK certificate*

- 你可以看到我们的确实是由 Lenovo 签发的。`PK` UEFI 变量也受到验证，每次变量更新都应使用对应 `PK` 变量中存储的当前证书的私钥进行签名。换句话说，如果平台所有者（或在 UEFI 术语中称为平台制造商）想要用新证书更新 `PK` 变量，则需要用当前 `PK` 变量中存储的证书对应的私钥对新证书缓冲区进行签名。

### UEFI Secure Boot: The Complete Picture

- 现在我们已经探索了 UEFI Secure Boot 所使用的 PKI 基础设施的完整层级，让我们把所有内容整合起来，看整体情况，如 Figure 17-8 所示。

![image](img/17fig08.jpg)

*Figure 17-8: UEFI Secure Boot verification flow*

- 在图的最上方，你可以看到根本信任根（UEFI Secure Boot 本身天然信任的组件，所有后续验证都基于此）：平台初始化固件和平台密钥。平台初始化固件是 CPU 复位后首先执行的代码，Secure Boot 隐式信任这段代码。如果攻击者 compromises（入侵/破坏）了 PI 固件，整个 Secure Boot 强制的信任链会被破坏。在这种情况下，攻击者可以修补实现 Secure Boot 镜像验证的任何 UEFI 模块，使其始终返回成功，从而让所有提供的 UEFI 镜像都通过验证。

- 因此，Secure Boot 的信任模型假设你已正确实现固件安全更新机制，该机制要求固件更新必须使用正确的签名键（该键必须不同于 PK）。这样，只有经过授权的 PI 固件更新才会发生，根本信任保持完整。

- 很明显，该信任模型不保护物理攻击者，他们可以直接对 SPI 闪存进行重写，植入恶意固件镜像并破坏 PI 固件。我们将在“Protecting Secure Boot with Verified and Measured Boot”章节的 page 338 上讨论如何防范固件的物理攻击。

- 在 Figure 17-8 的最上方，你可以看到平台制造商提供的平台密钥（platform key）具有与 PI 固件相同的固有信任级别。该密钥用于建立 PI 固件与平台制造商之间的信任。一旦平台密钥提供，平台固件允许制造商更新 KEKs，从而控制哪些镜像通过 Secure Boot 检查，哪些不通过。

- 在其下方，你可以看到 KEKs，它们负责建立 PI 固件与运行在平台上的操作系统之间的信任。当平台 KEK 在 UEFI 变量中被配置后，操作系统可以指定哪些镜像可以通过 Secure Boot 检查。例如，操作系统厂商可以使用 KEK 允许 UEFI 固件执行操作系统加载器。

- 在信任模型的最底部，你可以看到 `db` 和 `dbx` 数据库，它们由 KEKs 签名，包含用于 Secure Boot 直接完整性检查的镜像哈希和公钥证书。

### Secure Boot Policy

- 单独来看，Secure Boot 使用 `PK`、`KEK`、`db`、`dbx` 和 `dbt` 变量来指示平台是否信任可执行镜像，正如我们前面所见。然而，Secure Boot 验证结果的解释（即是否执行镜像）很大程度上取决于当前的策略。

- 本章节已经多次提到 Secure Boot 策略，但尚未深入说明其具体内容。下面我们来更详细地探讨这个概念。

- 简单来说，Secure Boot 策略决定平台固件在完成镜像验证后应采取哪些操作。固件可能执行镜像、禁止执行、延迟执行，或请求用户做出决定。

- Secure Boot 策略在 UEFI 规范中并未严格定义，因此是每个实现特有的，尤其是不同厂商的 UEFI 固件实现之间会有差异。本节将探讨我们在 Intel 的 EDK2 源码中实现的若干策略元素，该源码在 Chapter 15 中使用，你可以从 [`github.com/tianocore/edk2/`](https://github.com/tianocore/edk2/) 下载或克隆仓库。

- EDK2 中 Secure Boot 实现考虑的一个元素是可执行镜像的来源。镜像可能来自不同的存储设备，有些设备本身被视为受信任。例如，如果镜像从 SPI 闪存加载（即与 UEFI 固件位于同一存储设备上），平台可能会自动信任它。但如果攻击者能够篡改 SPI 闪存上的镜像，他们也可以篡改固件并完全禁用 Secure Boot。我们将在“Patching PI Firmware to Disable Secure Boot”章节的 page 335 上讨论此攻击。

- 相反，如果镜像从外部 PCI 设备加载（例如 Option ROM，预启动环境中从外部外设加载的特殊固件），则被视为不受信任，需要经过 Secure Boot 检查。

- 下面我们列出了一些决定镜像处理方式的策略定义。这些策略位于 EDK2 仓库的 `SecurityPkg\\SecurityPkg.dec` 文件中。每个策略为满足条件的镜像分配一个默认值。

  - `PcdOptionRomImageVerificationPolicy` 定义了加载为 Option ROM 的镜像（如 PCI 设备上的镜像）的验证策略，默认值为 `0x00000004`。

  - `PcdRemovableMediaImageVerificationPolicy` 定义了位于可移除介质（包括 CD‑ROM、USB、网络）上的镜像的验证策略，默认值为 `0x00000004`。

  - `PcdFixedMediaImageVerificationPolicy` 定义了位于固定介质设备（如硬盘）上的镜像的验证策略，默认值为 `0x00000004`。

- 除了上述策略，还有两条未在 `SecurityPkg\\SecurityPkg.dec` 文件中明确定义但被 EDK2 Secure Boot 实现使用的策略：

  - **SPI flash ROM policy** 定义了位于 SPI 闪存上的镜像的验证策略，默认值为 `0x00000000`。

  - **Other origin** 定义了除上述设备外的任何镜像的验证策略，默认值为 `0x00000004`。

> **NOTE**
>
> 请记住，这并不是 Secure Boot 用于镜像验证的完整策略列表。不同固件厂商可以根据需要修改或扩展此列表，加入自定义策略。

#### 默认策略值的描述

| 值 | 说明 |
| --- | --- |
| `0x00000000` | 始终信任镜像，无论是否签名，无论其哈希是否在 db 或 dbx 数据库中。 |
| `0x00000001` | 永不信任镜像。即使镜像拥有有效签名，也会被拒绝。 |
| `0x00000002` | 允许在出现安全漏洞时执行。即使镜像签名无法验证，或其哈希在 dbx 数据库中被列入黑名单，镜像仍会被执行。 |
| `0x00000003` | 在出现安全漏洞时延迟执行。镜像不会立即被拒绝，而是加载到内存中，执行会在重新评估其身份验证状态后才进行。 |
| `0x00000004` | 当 Secure Boot 未能使用 db 和 dbx 数据库验证镜像时，禁止执行。 |
| `0x00000005` | 在出现安全漏洞时询问用户。如果 Secure Boot 未能验证镜像，授权用户可决定是否信任该镜像。例如，启动时会显示用户消息提示。 |

从 Secure Boot 政策定义可以看出，所有从 SPI 闪存加载的镜像默认受信任，完全不进行数字签名验证。在其他情况下，默认值 `0x00000004` 强制要求签名验证，禁止执行任何未经认证的代码，包括作为 Option ROM 的镜像或位于可移除、固定或其他介质上的镜像。

### 防止使用 Secure Boot 的 Bootkits

在了解 Secure Boot 的工作原理后，我们来看一个具体的例子，说明它如何防止针对操作系统引导流的 Bootkits。我们不会讨论针对 MBR 和 VBR 的 Bootkits，因为正如 第 14 章 所述，UEFI 固件不再使用 MBR 和 VBR 这类对象（除非在 UEFI 兼容模式下），传统 Bootkits 无法破坏基于 UEFI 的系统。
