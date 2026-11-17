

表示对象可以通过资源策略设置为公共。以下示例策略允许全世界所有人读取存储桶，因为 Principal 被设置为 "*":

```
{
"Version": "2012-10-17",
"Statement": [
{
"Sid": "AnyoneCanRead",
"Effect": "Allow",
"Principal": "*",
"Action": ["s3:GetObject"],
"Resource": ["arn:aws:s3:::my-bucket/*"]
}
]
}
```

默认情况下，S3 中的所有内容对所有者都是私有的。如果要将前缀向全世界公开，则 Resource 更改为 arn:aws:s3:::my-bucket/some-prefix/*，同样，如果面向特定 IAM 用户或 IAM 组，则详细信息应放在策略的 principal 部分中。

存储桶策略也可以添加条件。让我们来看一个用例：组织希望保持存储桶公开，并将特定 IP 地址加入白名单。策略大致如下：

```
{
"Version": "2012-10-17",
"Statement": [
{
"Sid": "ParticularIPRead",
"Effect": "Allow",
"Principal": "*",
"Action": ["s3:GetObject"],
"Resource": ["arn:aws:s3:::my-bucket/*"],
"Condition": {
"NotIpAddress": {"aws:SourceIp": "2.3.3.6/32"}
}
}
]
}
```

更多示例可在 AWS S3 开发者指南中找到，链接如下：

https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html.

阻止公共访问是赋予存储桶所有者的单独设置，用于避免存储桶策略中出现任何错误。在实际场景中，可能会因误操作通过存储桶策略将存储桶设为公开；为避免此类错误或数据泄露，AWS 提供了此设置。它提供了进一步的安全级别，与存储桶策略无关。您可以在创建存储桶时选择此设置，也可以在创建存储桶后进行设置。

身份策略专用于 IAM 用户和 IAM 角色。当 IAM 身份（用户或角色）请求访问资源时，会验证身份策略。默认情况下拒绝所有请求。如果身份意图访问任何服务、资源或操作，则必须通过身份策略显式提供访问权限。以下示例策略可以附加到 IAM 用户，该 IAM 用户将被允许在特定区域（本示例中的 us-east-1）内拥有完整的 RDS 访问权限：

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "rds:*",
            "Resource": ["arn:aws:rds:us-east-1:*:*"]
        },
        {
            "Effect": "Allow",
            "Action": ["rds:Describe*"],
            "Resource": ["*"]
        }
    ]
}
```

访问控制列表 (ACL) 用于授予高级权限，通常用于向其他 AWS 账户授予访问权限。ACL 是存储桶或对象的子资源之一。可以通过 ACL 快速将存储桶或对象设为公开。AWS 不建议这样做，也不应期望考试中会涉及此内容。了解此知识点是有好处的，但它不如 S3 存储桶策略灵活。

现在，让我们在下一节中学习保护数据的方法。

## 保护 Amazon S3 上的数据

在本节中，您将学习如何记录对象的每个版本。除了持久性，Amazon 还提供多种技术来保护 S3 中的数据。其中一些技术涉及启用版本控制和加密对象。

版本控制可帮助您在当前对象在更新、删除或 put 操作期间出现问题时回滚到先前版本。

通过加密，您可以控制对象的访问权限。您需要相应的密钥才能读取和写入对象。您还将学习删除操作的多重身份验证 (MFA)。

Amazon 还允许 **Cross-Region Replication (CRR)** 在另一个区域中保持对象的副本，可用于任何灾难期间的数据备份、进一步冗余或增强不同区域的数据访问速度。

## 应用存储桶版本控制

现在让我们了解如何通过一些实践示例启用存储桶版本控制。可以在从 AWS S3 控制台创建存储桶时应用存储桶版本控制：

- 1. 要从命令行启用存储桶的版本控制，必须先创建存储桶，然后才能启用版本控制，如以下示例所示。在此示例中，我创建了存储桶 version-demo-mlpractice，并通过 put-bucket-versioning 命令启用了版本控制：

```
$ aws s3 mb s3://version-demo-mlpractice/
$ aws s3api put-bucket-versioning --bucket version-demo-mlpractice --versioning-configuration Status=Enabled
$ aws s3api get-bucket-versioning --bucket version-demo-mlpractice
{
    "Status": "Enabled"
}
```

- 2. 您未对该存储桶创建任何加密类型。因此，如果运行 aws s3api get-bucket-encryption --bucket version-demo-mlpractice，则会输出以下错误：
  - **未找到服务器端加密配置**

- 3. 服务器端加密 (SSE) 可以在从 AWS S3 控制台创建存储桶时应用。这称为存储桶默认加密。您也可以通过命令行使用 put-bucket-encryption API 应用 SSE。命令如下所示：

```
$ aws s3api put-bucket-encryption --bucket version-demo-mlpractice --server-side-encryption-configuration '{"Rules": [{"ApplyServerSideEncryptionByDefault": {"SSEAlgorithm": "AES256"}}]}'
```

- 4. 可以使用以下命令进行验证：aws s3api get-bucket-encryption --bucket version-demo-mlpractice。

您将在下一节中了解更多有关加密的内容。

## 对存储桶应用加密

您还需要了解在存储桶上启用版本控制有何帮助。存在一种用例：文件会定期更新，并为同一文件创建版本。要模拟此场景，请尝试以下示例：

- 1. 在此示例中，您将创建一个文件，并在其中写入版本。您将覆盖并检索它以检查该文件中的版本：

```
$ echo "Version-1">version-doc.txt
$ aws s3 cp version-doc.txt s3://version-demo-mlpractice
$ aws s3 cp s3://version-demo-mlpractice/version-doc.txt check.txt
$ cat check.txt
Version-1
$ echo "Version-2">version-doc.txt
$ aws s3 cp version-doc.txt s3://version-demo-mlpractice
$ aws s3 cp s3://version-demo-mlpractice/version-doc.txt check.txt
$ cat check.txt
Version-2
```

- 2. 检索时，您得到的是文件的最新版本，在此示例中即 Version-2。要检查每个版本及其最新版本，S3 提供了 list-object-versions API，如下所示。从 JSON 结果中，您可以推断出最新版本：

```
$ aws s3api list-object-versions --bucket version-demo-mlpractice
{
    "Versions": [
    {
        "ETag": "\\b6690f56ca22c410a2782512d24cdc97\\",
        "Size": 10,
        "StorageClass": "STANDARD",
        "Key": "version-doc.txt",
        "VersionId": "70wbLG6BMEBQhCXmwsriDgQoXafFmgGi",
        "IsLatest": true,
        "LastModified": "2020-11-07T15:57:05+00:00",
        "Owner": {
        "DisplayName": "baba",
        "ID": "XXXXXXXXXXX"
        }
    },
    {
        "ETag": "\\5022e6af0dd3d2ea70920438271b21a2\\",
        "Size": 10,
        "StorageClass": "STANDARD",
        "Key": "version-doc.txt",
        "VersionId": "fliC.9L.MsP00tIb.sUMnfOEae240sIW",
        "IsLatest": false,
        "LastModified": "2020-11-07T15:56:27+00:00",
        "Owner": {
        "DisplayName": "baba",
        "ID": "XXXXXXXXXXX"
        }
    }
    ]
}
```

- 3. 可能存在需要回滚到当前对象较早版本的情况。在前面的示例中，最新版本是 Version-2。您可以通过将 VersionId 子资源解析为 get-object API 调用并再次上传该对象，将任何所需版本设为最新或当前版本。另一种方法是在 delete-object API 请求中将 versionId 传递给 --version-id 参数，删除当前或最新版本。有关 API 的更多详细信息，请参阅：https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-object.html。

- 4. 当在启用版本控制的存储桶中删除对象时，它不会从存储桶中删除该对象。它只是创建一个名为 DeleteMarker 的标记。示例如下：

```
$ aws s3api delete-object --bucket version-demo-mlpractice --key version-doc.txt
{
	"DeleteMarker": true,
	"VersionId": "BKv_Cxixtm7V48MWqBO_KUkKbcOaH5JP"
}
```

- 5. 这意味着对象未被删除。您可以使用以下命令列出它：aws s3api list-object-versions --bucket version-demo-mlpractice

- 6. 现在存储桶中没有名为 version-doc.txt 的对象，您可以使用 aws s3 ls 命令进行验证，因为该标记已成为对象的当前版本并带有新 ID。如果尝试检索已删除的对象（即删除标记充当对象的当前版本），则会收到 404 错误。因此，在启用版本控制的存储桶中永久删除对象的唯一方法是分别使用对象的版本 ID 删除该对象。如果需要恢复对象，则可以通过删除删除标记（即 VersionId）来检索同一对象，如以下示例命令所示。简单的删除请求（不带版本 ID）不会删除删除标记，而是会创建另一个带有唯一版本 ID 的删除标记。因此，同一对象可能存在多个删除标记。在此需要注意的是，这将消耗您的存储空间并产生费用：

```
$ aws s3 ls s3://version-demo-mlpractice/
$ aws s3api delete-object --bucket version-demo-mlpractice --key version-doc.txt --version-id BKv_Cxixtm7V48MWqBO_KUkKbcOaH5JP
{
	"DeleteMarker": true,
	"VersionId": "BKv_Cxixtm7V48MWqBO_KUkKbcOaH5JP"
}
```

- 7. 现在列出存储桶时，可以看到旧对象：

```
$ aws s3 ls s3://version-demo-mlpractice/
2020-11-07 15:57:05	10	version-doc.txt
```

由于您已经涵盖了考试主题并练习了大多数所需概念，应删除存储桶中的对象，然后删除存储桶以节省成本。此步骤会删除对象的版本，从而永久移除该对象。

- 8. 在此，先通过版本 ID 删除最新版本，然后删除另一个版本 ID：

```
$ aws s3api delete-object --bucket version-demo-mlpractice --key version-doc.txt --version-id 70wL6G6MBEQhQXmwsriDgQoXafFmgGi
$ aws s3api delete-object --bucket version-demo-mlpractice --key version-doc.txt --version-id fliC.9L.MsP0OtIb.sUMnfoOeAe240sIW
$ aws s3api list-object-versions --bucket version-demo-mlpractice
```

现在您可以清楚地看到空存储桶了。

## 重要提示

