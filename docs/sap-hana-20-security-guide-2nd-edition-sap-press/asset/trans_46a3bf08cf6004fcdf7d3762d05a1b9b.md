

# 管理 SAP HANA 数据库中的证书

## 添加证书

```
CREATE CERTIFICATE FROM 
'-----BEGIN CERTIFICATE-----
ERGJKjCCAz6gAwIDGDddtJHdfDFVmGMA0666*GSIb3DQEBBQUAMHkx89SDFGfV
cvdfSFGydfgDGGjgh5$5DSFghghdsdfs4%^SDfsdgfdgsdf++dffYTFTDFDSd
2FFgtDSFSDFdsfds==
-----END CERTIFICATE-----' 
COMMENT 'E-Corp Certificate CA Client Communications';
```

**Listing 13.1** 将证书添加到 SAP HANA 数据库存储的 SQL 代码

要删除尚未添加到证书集合的证书，请使用 `DROP CERTIFICATE` SQL 语句。例如，执行以下 SQL 语句以删除证书 ID 为 123454 的证书：

```
DROP CERTIFICATE 123454;
```

您可以查询系统视图以确定先前导入证书的证书 ID。以下 SQL 语句将返回当前导入到系统中的所有证书：

```
SELECT * FROM SYS.CERTIFICATES;
```

除了使用 SQL，您还可以使用 SAP HANA cockpit 来管理证书。您可以在“安全相关链接”磁贴下找到管理界面的链接以及“管理证书”链接。一旦您有权访问证书存储管理界面，您将看到先前导入的证书列表，从“颁发给”列开始。单击单个证书以查看更多详细信息、查看证书的原始 PEM 格式或删除证书。您还可以使用证书列表右侧圆圈内的 x 图标删除证书。

您可以使用证书列表上方右侧的“导入”链接导入证书。单击导入链接后，将出现“导入受信任证书”窗口，如 [Figure 13.2](#13_001.html#f13.2) 所示。证书可以直接使用“从文件导入”部分导入。所选文件必须为 PEM 格式，并且位于浏览器操作系统的本地。或者，您也可以在“粘贴内容”部分中粘贴 PEM 格式的原始证书文本。添加自定义注释以描述证书的其他详细信息。

[![Importing Certificates Using the SAP HANA Cockpit](bilderklein/klein13_002.png)](img-f13.2.html)

**Figure 13.2** 使用 SAP HANA Cockpit 导入证书

接下来，我们需要将证书分配给证书集合。

## 创建/删除证书集合或 PSE

证书必须与 PSE 关联，因此您需要先创建一个 PSE，然后才能分配证书的用途。要创建 PSE，请执行 `CREATE PSE` SQL 命令。要执行此 SQL 命令，被授予者必须拥有 `TRUST ADMIN` 系统权限。以下语句提供了一般语法和示例：

```
CREATE PSE <PSE_NAME>;
CREATE PSE "BI_SSO_SAM_CERT";
```

要按 PSE 查看证书列表，可以查询 `PSE_CERTIFICATES` 系统视图。例如，要查看 SAP HANA 系统中的所有证书集合或 PSE，请使用以下 SQL 查询：

```
SELECT * FROM PSE_CERTIFICATES;
```

要查看系统中定义的 PSE 列表，请执行以下 SQL 语句：

```
SELECT * FROM PSES;
```

要删除 PSE，请使用以下 SQL 命令；第一行提供语法，第二行提供示例：

```
DROP PSE <PSE_NAME>;
DROP PSE "BI_SSO_SAM_CERT";
```

除了使用 SQL，您还可以使用 SAP HANA cockpit 来管理证书集合。您可以在“安全相关链接”磁贴下找到管理界面的链接以及“管理证书集合”链接。将出现“证书集合”窗口，如 [Figure 13.3](#13_001.html#f13.3) 所示。窗口左侧是一个带有先前定义的证书集合列表的窗格。单击每个列出的证书集合，以在右侧查看与其相关的详细信息，包括集合中的关联证书列表以及证书集合的用途等其他详细信息。我们将在下一节中更详细地回顾该界面，演示如何将证书添加到集合中，以及如何使用 SAP HANA cockpit 设置证书用途。

[![SAP HANA Cockpit Certificate Collection Interface](bilderklein/klein13_003.png)](img-f13.3.html)

**Figure 13.3** SAP HANA Cockpit 证书集合界面

接下来，您需要将证书分配给 PSE。

## 管理 PSE 中的证书

您可以使用 SQL 命令从 PSE 或证书集合中添加和删除证书。要将证书添加到 PSE，请使用 `ALTER PSE` SQL 命令。要修改 PSE，您必须是 PSE 的所有者。或者，被授予者必须在证书集合或 PSE 上拥有 `ALTER` 对象权限。例如，以下 SQL 将授予对 PSE 的访问权限：

```
GRANT ALTER ON PSE "BI_SSO_SAM_CERT" TO SECURITY_ADMINS;
```

要将现有证书添加到 PSE，请使用以下 SQL 语句：

```
ALTER PSE <PSE> ADD CERTIFICATE <CERTIFICATE ID>
```

在示例中，将 `<PSE>` 变量替换为您的 PSE 名称，并将 `<CERTIFICATE ID>` 变量替换为先前导入到 SAP HANA 系统中的证书 ID。

要从 PSE 中删除证书，请使用以下 SQL 命令：

```
ALTER PSE <PSE> DROP CERTIFICATE <CERTIFICATE ID>
```

在示例中，将 `<PSE>` 变量替换为您的 PSE 名称。将 `<CERTIFICATE ID>` 变量替换为与 PSE 关联的证书 ID。

除了使用 SQL，您还可以使用 SAP HANA cockpit 从证书集合中添加和删除证书。您可以在“安全相关链接”磁贴下找到管理界面的链接以及“管理证书集合”链接。在界面中，选择现有证书集合以查看集合中的详细信息和关联证书，如 [Figure 13.4](#13_001.html#f13.4) 所示。

[![Adding Certificates to a Collection Using the SAP HANA Cockpit](bilderklein/klein13_004.png)](img-f13.4.html)

**Figure 13.4** 使用 SAP HANA Cockpit 将证书添加到集合

要添加证书，请找到证书列表上方的“添加证书”按钮。将出现“选择证书”窗口，您可以在其中搜索并选择 SAP HANA 数据库中的现有证书。[Figure 13.4](#13_001.html#f13.4) 显示将现有证书添加到 none 集合的位置。要从集合中删除证书，请单击列出的证书右侧圆圈内的 x 图标。“设置为自有证书”按钮将允许您直接将新证书导入数据库，同时将其添加到集合中。

接下来，您需要定义 PSE 的用途。

## 定义 PSE 的用途

数据库内证书管理的最后一步是定义 PSE 及其证书的用途。PSE 的用途指示其将如何使用，您提供的用途名称对数据库中的特定用例具有意义。例如，用途 `LDAP` 告诉数据库该证书用于信任配置的 LDAP 提供程序并通过 TLS 与其通信。您可以使用数据库内 PSE 进行身份验证或 TLS 安全通信。例如，如果您使用 PSE 进行带有 SAML 的 SSO，则必须将 PSE 的用途定义为 `SAML`。系统允许 [Table 13.1](#13_001.html#t13.1) 中列出的用途被分配。

| Purpose | Use |
| --- | --- |
| SAML | If the PSE is used for SAML SSO authentication |
| SAP LOGON | If the PSE is used for SAP assertion ticket authentication |
| X509 | If the PSE is used for X.509 certificate-based authentication |
| SSL/TLS | If the PSE is used to secure communications with JDBC, ODBC, or SAP HANA administration tool connections |

