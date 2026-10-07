
现在你已经创建了一个用于对称加密的密钥，让我们来看看如何使用它来加密内容。

## 使用对称密钥加密内容

以下是一个使用现有密钥进行加密的命令：

```
gcloud kms encrypt \
--key key \
--keyring key-ring-name \
--location location \
--plaintext-file file-with-data-to-encrypt \
--ciphertext-file file-to-store-encrypted-data
```

将 `key` 替换为用于加密的密钥名称。将 `key-ring-name` 替换为密钥所在的密钥轮名称。将 `location` 替换为密钥轮所在的 Cloud KMS 地位置。将 `file-with-data-to-encrypt` 和 `file-to-store-encrypted-data` 替换为读取明文数据和保存加密输出的本地文件路径（也包括实际文件名）。

此命令将生成一个包含加密数据的文件。该文件的名称即为你你为 `--ciphertext-file` 参数提供的名称。

现在你已经了解了如何加密内容，让我们来看看如何解密它。

## 使用对称密钥解密内容

以下是一个使用现有密钥进行解密的命令：

```
gcloud kms decrypt \
--key key \
--keyring key-ring-name \
--location location \
--ciphertext-file file-path-to-encrypted-data \
--plaintext-file file-path-to-store-plaintext
```

将 `key` 替换为用于加密的密钥名称。将 `key-ring-name` 替换为密钥所在的密钥轮名称。将 `location` 替换为密钥轮所在的 Cloud KMS 地位置。将 `file-path-with-encrypted-data` 和 `file-path-to-store-plaintext` 替换为读取明文数据和保存加密输出的本地文件路径（也包括实际文件名）。

此命令将生成一个包含解密数据的文件。该文件的名称为你为 `--plaintext-file`提供的名称。

## 非对称密钥加密

现在你已经了解了使用 Cloud KMS 进行对称密钥加密和解密，让我们来看看如何使用非对称密钥加密。

## 非对称密钥加密

本节描述了使用非对称密钥加密和解密数据的流程。非对称密钥加密涉及密钥对（公钥和私钥对）。如名所示，私钥是不共享的，而公钥是共享的。此工作流中有两个参与者——发送者接收者。发送者使用接收者的公钥创建密文，然后接收者使用其持有的私钥解密密文。只有知道私钥的人才能解密密文。

Cloud KMS 提供以下与非对称加密相关的功能：

- 创建用于 `ASYMMETRIC_DECRYPT` 非对称密钥的能力。有关 Cloud KMS 支持的算法信息，请参阅 Google Cloud 文档中的非对称加密算法。
- Cloud KMS 密钥还支持 `ASYMMETRIC_SIGN` (ECC 和 RSA)。
- 获取非对称密钥公钥的能力。你使用公钥加密数据。Cloud KMS 不提供分析加密数据的方法。相反，你使用公开的 SDK 和工具（如 OpenSSL）来加密数据。这些 SDK 和工具需要你从 Cloud KMS 获取公钥。
- 使用非对称密钥解密数据的能力。

现在，让我们查看执行非对称加密和签名的步骤。与创建对称密钥类似，为了创建非对称密钥，你首先需要创建一个密钥轮。密钥轮决定了密钥的位置。让我们开始吧。

### 第 1 步：创建密钥轮

使用以下命令为你的非对称密钥创建密钥轮：

```
gcloud kms keyrings create key-ring-name \
  --location location
```

将 `key-ring-name` 替换为密钥轮名称。将 `location` 替换为 Cloud KMS 地位置。

### 第 2 步：创建非对称解密密钥

按照以下步骤在指定的密钥轮和位置创建非对称解密密钥。这些示例使用了软件保护级别和 `rsa-decrypt-oaep-2048-sha256` 算法。当你首次创建密钥时，密钥的初始版本状态为 `pending`（等待中）。当状态变为 `enabled`（可用）时，你可以：

将 `key` 替换为新密钥。将 `key-ring-name` 替换为密钥所在的现有密钥轮名称。将 `location` 替换为 KMS 位置。

### 第 3 步：（可选）：创建非对称签名密钥

按照以下步骤在指定的密钥轮和位置创建非对称签名密钥。以下命令使用了软件保护级别和 `rsa-sign-pkcs1-2048-sha256` 算法。当你首次创建密钥时，密钥的初始版本状态为 `pending`。当状态变为 `enabled` 时，你可以：

```
gcloud kms keys create key \
--keyring key-ring-name \
--location location \
--purpose "asymmetric-signing" \
--default-algorithm "rsa-sign-pkcs1-2048-sha256"
```

现在，让我们了解如何使用非对称密钥。

## 使用非对称密钥加密数据

本节提供了在命令行中运行的示例。我们使用 OpenSSL 来加密数据。Cloud Shell 预装了 OpenSSL，因此你可以在 Cloud Shell 中直接尝试。

注意：你不能对用途为 `ASYMMETRIC_SIGN` 的密钥执行此过程。macOS 上安装的 OpenSSL 版本不支持解密数据所需的标志。要在 macOS 上遵循这些步骤，请通过 Homebrew 安装 OpenSSL。

### 第 1 步：下载公钥

运行以下命令下载你之前创建的对称密钥的公钥部分：

```
gcloud kms versions get-public-key key-version \
  --key key \
  --keyring key-ring-name \
  --location location \
  --output-file public-key-path
```

将 `key-version` 替换为密钥版本。将 `key` 替换为用于加密的密钥。将 `key-ring-name` 替换为密钥所在的密钥轮名称。将 `location` 替换为密钥轮所在的 Cloud KMS 位置。将 `public-key-path` 替换为保存公钥的位置。

现在，使用你下载的公钥加密数据：

```
openssl pkey -in cleartext-data-file \
  --encrypt \
  --pubin \
  --inkey public-key-path \
  -pkeyopt rsa_padding_mode:oaep \
  -pkeyopt rsa_oaep_md:sha256 \
  -pkeyopt rsa_mgf1_md:sha256 \
  -out encrypted-data-file
```

将 `cleartext-data-file` 替换为要加密的明文数据。将 `public-key-path` 替换为公钥路径。将 `encrypted-data-file` 替换为保存加密输出的文件。

## 使用非对称密钥解密数据

我们将使用非对称密钥的私钥部分来解密数据。运行解密 gcloud 命令：

```
gcloud kms asymmetric-decrypt \
  --version key-version \
  --key key \
  --keyring key-ring-name \
  --location location \
  --ciphertext-file file-path-with-encrypted-data \
  --plaintext-file file-path-to-store-plaintext
```

将 `key-version` 替换为密钥版本，或省略 `--version` 自动检测版本。将 `key` 替换为用于解密的密钥名称。将 `key-ring-name` 替换为密钥所在的密钥轮名称。将 `location` 替换为密钥轮所在的 Cloud KMS 地位置。将 `file-path-with-encrypted-data` 和 `file-path-to-store-plaintext` 替换为读取加密数据和保存解密输出的本地文件路径。

解密后的文本将位于 `plaintext-file`。

我们查看了使用 KMS 生成密钥的一些常用操作。现在让我们来看看另一种高级选项：将自己的密钥带到云端，某些组织为了合规性可能会这样做。

## 导入密钥 (BYOK)

Google 允许你自带加密密钥材料。你可以使用软件或 Cloud HSM 保护级别进行导入。我们将提供执行此操作的步骤说明。在此之前，让我们了解导入密钥的原因：

- 你可能在使用在本地或外部 KMS 创建的密钥。
- 如果你将应用程序迁移到 Google Cloud，或者为现有的 Google Cloud 应用添加加密支持，可以将相关密钥导入 Cloud KMS。
- 作为导入的一部分，Cloud KMS 会生成一个包装密钥（公钥/私钥对），并使用支持的导入方法。使用该包装密钥加密你的密钥材料可以确保其在传输过程中的安全。
- 该 KMS 公包装密钥用于在客户端加密加密要导入的密钥。该公钥对应的私钥存储在 Google Cloud 内部，并在密钥到达 Google Cloud 项目后进行解包。
