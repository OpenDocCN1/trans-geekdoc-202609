

## 导入密钥 (BYOK)

- 除了这些选项外，请确保您也遵循以下指南：

- 验证您的密钥算法和长度是否受 Google Cloud KMS 支持。允许的算法取决于密钥用于对称加密、非对称加密还是非对称签名，以及它是存储在软件还是 HSM 中。您将在导入请求中指定密钥的算法。

- 此外，您还必须验证密钥的编码方式，并在时进行调整。

现在让我们开始学习向 Google Cloud 导入密钥的说明。为了简单起见，我们将使用 `gcloud`。

## 第一步：创建一个空密钥

- 1. 在 Google Cloud 控制台中创建一个项目，并启用 Cloud KMS。

- 2. 如果您没有要导入的密钥，但想测试导入密钥，可以使用以下命令在本地系统创建一个对称密钥：

```bash
openssl rand 32 > ${HOME}/test.bin
```

> 注意
> 此密钥仅用于测试。通过这种方式创建的密钥可能不适用于生产环境。

- 3. 在您选择的区域内创建一个新密钥。

- 4. 使用以下参数创建一个类型为导入密钥（imported key）的新密钥：

I. 名称：ext-key-3
II. 保护级别：软件（Software）
III. 用途：对称加密/解密
IV. 旋转周期：手动（Manual）

- 5. 创建了一个没有版本的空密钥；您将被重定向到创建密钥版本。

- 6. 使用以下 `gcloud` 命令创建密钥版本。我们将创建一个对称密钥：

```bash
gcloud kms keys create-key-4 --location us-central \
--keyring external-central-key-ring --purpose encryption \
--skip-initial-version-creation
```

- 7. 创建一个新的导入作业（import job）。

- 8. 下载包装密钥（wrapping key）。

此密钥尚无法使用，因为它是一个空壳，用于存放您后续步骤中导入的密钥材料。现在，您有两个选择：

- 上传您预包装的加密密钥。

- 使用 `gcloud` 命令将您的密钥提供给作业，作业会自动对其进行包装。您将根据是想让 `gcloud` 命令行工具自动包装密钥还是手动包装密钥，使用不同的标志来发出导入请求。我们将使用 `gcloud` 选项，因为它易于理解。

## 第二步：使用导入作业导入密钥

- 1. 设置导出 `CLOUDSDK_PYTHON_SITEPACKAGES=1`，否则您将看到以下错误：

无法加载 Pyca cryptography 库。该库未安装，或者未为 Google Cloud SDK 启用站点包（site packages）。请咨询 https://cloud.google.com/kms/docs/crypto 获取更多指令。

- 2. 确保您的命令已设置了上述环境变量：

```bash
echo $CLOUDSDK_PYTHON_SITEPACKAGES
```

- 3. 执行命令将您的密钥上传到 Cloud KMS：

```bash
user@cloudshell:~ $ gcloud kms keys versions import --import-job ext-key-import-job --location us-central --keyring external-central-key-name --ext-key-4 --algorithm google-symmetric-encryption --target-file ${HOME}/test.bin --public-key-file /home/user/ext-key-import-job pub --verbosity info
```

现在您将看到关于显示内容的输出：

```
INFO: Display format: "default"
algorithm: GOOGLE_SYMMETRIC_ENCRYPTION
createTime: "2020-04-08T22:25:46.597631370Z"
importJob: projects/PROJECT_ID/locations/us-central/keyRings/central-key-name/importJobs/ext-key-import-job
name: projects/PROJECT_ID/locations/us-central/keyRings/external-central-key-name/cryptoKeys/ext-key-1/
protectionLevel: SOFTWARE
state: PENDING_IMPORT
```

- 4. 等待密钥版本处于 ENABLED（已启用）状态，然后使用以下 `gcloud` 命令将其设置为主版本（primary）：

```bash
gcloud kms keys set-primary-version ext-key-1 --version=1 \
  --keyring=external-central-key-name --location=us-central1
```

Cloud KMS 只使用密钥的主版本。现在您已经设置了它，让我们继续使用它。

## 第三步：验证密钥加密和解密

- 1. 创建一个包含一些明文的 `secrets.txt` 文件。使用 `gcloud` 对其加密：

```bash
gcloud kms encrypt --ciphertext-file=secrets.txt.enc \
  --plaintext-file=secrets.txt --key=ext-key-4 --keyring=external-central-key-name --location=us-central1
```

- 2. 现在使用以下命令使用相同的密钥对其解密：

```bash
gcloud kms decrypt --ciphertext-file=secrets.txt \
  --plaintext-file=secrets.txt.dec --key=ext-key-1 \
  --keyring=external-central-key-name --location=us-central1
```

验证解密后的内容与明文相同。本教程演示了您可以自备密钥材料来对其加密和解密。

现在我们了解了可以在 Cloud KMS 中使用的几种类型的密钥，让我们来了解密钥的生命周期。

## 密钥管理

在运行负载时，您需要管理密钥的生命周期。美国国家标准与技术研究院（NIST）特别出版物（SP）800-57 第1部分描述了密钥生命周期，分为四个阶段：操作前、操作中、操作后和销毁。

以下章节提供了 NIST 生命周期函数到 Google Cloud KMS 生命周期函数的映射。

- 1. 操作前生命阶段映射到：
    - I. NIST 8.1.4 密钥材料安装函数：等同 Cloud KMS 操作是导入。
    - II. NIST 8.1.5 密钥建立函数：等同 Cloud KMS 操作是创建。

- 2. 操作生命阶段映射到：
    - I. NIST 8.2.1 正常操作存储函数：等同 Cloud KMS 操作是在软件、HSM 或外部保护级别创建。
    - II. NIST 8.2.3 密钥变更函数：等同 Cloud KMS 操作是旋转。

- 3. 操作后生命阶段映射到：
    - I. NIST 8.3.4 密钥销毁函数：等同 Cloud KMS 操作是销毁（以及恢复）。

此外，Cloud KMS 提供了禁用密钥的功能。如果您发现需要，可以重新启用密钥。要授予管理权限但不授予加密或解密权限，请授予 Cloud KMS Admin (roles/cloudkms.admin) 角色。

记住 IAM 强制执行两个基本原则：

- 职责分离原则
- 最小权限原则

我们已经查看了 Cloud KMS 的各种角色和权限；现在让我们来看看如何管理的最佳实践：

- 对于小型组织，每个项目团队可以管理自己的 Cloud KMS 以及安全团队。
- 对于大型或复杂的组织，您可能会采取如下方法：

## Cloud HSM

- 为安全团队成员授予所有项目的 Cloud KMS Admin (roles/cloudkms.admin) 。如果不同团队处理密钥的不同方面，可以授予他们更细粒度的角色，例如 Cloud KMS 导入者 (roles/cloudkms.importer)。

- 为能够读取或写入加密数据的用户或服务账户授予 Cloud KMS 加密/解密者 (roles/cloudkms.cryptKeyEncrypterDecpter)。

- 为需要查看非对称加密公钥的用户或服务账户授予 Cloud KMS 公钥查看者 (roles/cloudkms.publicKeyViewer)。

- 对于使用 VPC 服务控制边界的项目，我们建议为边界准备单独 Cloud KMS 项目。

Cloud HSM 是一种云托管的 HSM 服务，允许您在通过 FIPS 140-2 第 3 认证的 HSM 集群中托管密钥并执行加密操作。Cloud HSM 集群由 Google 为您管理；您无法访问物理设备。您不需要为多区域应用程序对其进行补丁或扩展。Cloud HSM 使用 Cloud KMS 作为前端与 Cloud HSM 后端进行交互。

