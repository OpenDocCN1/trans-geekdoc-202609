

- 数据可以从多个设备生成，包括移动设备或物联网、Web日志、社交媒体、事务数据和在线游戏。
- 可使用轮询服务、通过与AWS Lambda集成的API网关收集数据，或通过AWS Kinesis、AWS托管的Kafka或Kinesis Firehose等流来收集产生的海量数据。如果你有本地数据库并希望将该数据迁移到AWS，则可以选择AWS DMS。你可以通过AWS DataSync将本地数据同步到Amazon S3、Amazon EFS或Amazon FSx。AWS Snowball用于收集/传输数据进出AWS。
- 下一步涉及存储数据。你在上一章中了解了一些用于此目的的服务，例如S3、EBS、EFS、RDS、Redshift和DynamoDB。
- 了解数据存储需求后，可以设计一个ETL作业，将结构化或非结构化数据提取-转换-加载或提取-加载-转换为所需格式，以便进行进一步分析。例如，你可以使用AWS Lambda实时转换数据并将转换后的数据存储在S3中，或者可以在EMR集群上运行Spark应用程序来转换数据并将其存储在S3、Redshift或RDS中。
- AWS中有许多服务可用于对转换后的数据进行分析，例如EMR、Athena、Redshift、Redshift Spectrum和Kinesis Analytics。
- 数据分析完成后，你可以使用AWS QuickSight将其可视化，以了解模式或趋势。数据科学家或机器学习专业人员希望应用统计分析来更好地了解数据分布。业务用户使用统计分析来准备报告。你将在第5章“数据理解与可视化”中学习和探索各种展示和可视化数据的方法。

从传统数据管道中你了解到，ETL主要涉及在服务器上编写和维护代码，以确保一切顺利运行。如果数据格式以任何方式发生变化，则需要更改代码，这会导致目标架构发生变更。如果数据源发生变化，代码也必须能够处理这种情况，这会带来额外开销。你是否应该编写代码来识别数据源中的这些变化？你是否需要一个系统来适应变化并为你发现数据？这些问题的答案是肯定的，为此，你可以使用AWS Glue。现在，你将了解AWS Glue为何如此流行。

## AWS Glue的功能

AWS Glue是AWS上的完全托管的无服务器ETL服务。它具有以下功能：

- 它通过连接到数据源自动发现和分类你的数据，并生成数据目录。
- 诸如Amazon Athena、Amazon Redshift和Amazon EMR之类的服务可以使用数据目录查询数据。
- AWS Glue生成ETL代码，该代码是Python或Scala中Spark的扩展，同样可以进行修改。
- 它会自动扩展，以匹配你的Spark应用程序需求来运行ETL作业并将数据加载到目标位置。

AWS Glue拥有数据目录，这是其成功的秘诀。它有助于从数据源发现数据并了解其相关信息：

- 数据目录会自动发现新数据并提取架构定义。它检测架构变更和版本表。它检测Amazon S3上的Apache Hive风格分区。
- 数据目录内置了用于常见数据类型的分类器。可以使用Grok表达式编写自定义分类器。分类器有助于检测架构。
- Glue爬虫可以临时运行，也可以按计划运行，以更新Glue数据目录中的元数据。Glue爬虫必须与具有足够权限以读取数据源（如Amazon RDS、Redshift和S3）的IAM角色相关联。

现在你对AWS Glue的用途有了简要了解，继续运行以下示例进行实践。

### 使用AWS Glue数据目录组件进行实践

在此示例中，你将创建一个作业，使用AWS Glue将数据从S3复制到Redshift。我的所有组件都在us-east-1区域中创建。首先创建一个存储桶：

1. 导航到AWS S3控制台并创建一个存储桶。我已将存储桶命名为aws-glue-example-01。
2. 单击“创建文件夹”并将其命名为input-data。
3. 导航到文件夹内部，单击上传按钮上传sales-records.csv数据集。数据可在以下GitHub位置找到：https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter03/AWS-Glue-Demo/input-data。

将数据上传到S3存储桶后，现在创建一个VPC，你将在其中创建Redshift集群。

4. 通过访问 https://console.aws.amazon.com/vpc/home?region=us-east-1# URL导航到VPC控制台，然后单击左侧菜单中的端点。单击创建端点，然后按如下所示填写字段：
   - 服务类别：AWS services
   - 选择服务：com.amazonaws.us-east-1.s3（网关类型）
   - VPC：选择默认VPC（在此默认VPC中将创建你的Redshift集群）
5. 保持其他字段不变，单击创建端点。
6. 从VPC控制台单击安全组。为你的安全组命名，例如redshift-self，并选择默认VPC下拉菜单。提供适当的描述，例如Redshift安全组。单击创建安全组。
7. 单击操作下拉菜单并选择编辑入站规则。单击添加规则，然后按如下所示完成字段：
   - 类型：All traffic
   - 源：自定义
   - 在搜索字段中，选择相同的安全组（redshift-self）

8. 单击保存规则。

现在，创建你的Redshift集群。

9. 导航到Amazon Redshift控制台。单击**创建集群**，完成如*图3.1*中所示的高亮字段：

![](img/87c29232224b00f5a8bba6a66a391700_74_0.png)

图3.1 – Amazon Redshift创建集群屏幕的截图

10. 向下滚动，使用你自己的值填写*图3.2*中显示的高亮字段：

#### 数据库配置

数据库名称（可选）
指定数据库名称以创建其他数据库。
glue-dev
名称必须为1-64个字母数字字符（仅限小写），且不能是保留字。

数据库端口（可选）
数据库接受入站连接的端口号。创建集群后无法更改端口。
5439
端口必须为数字（1150-65535）。

主用户名
输入DB实例主用户的登录ID。
awsuser
名称必须为1-128个字母数字字符，且不能是保留字。

主用户密码
******
☐ 显示密码
● 主密码必须为8 - 64个字符。● 该值必须至少包含一个大写字母。
● 该值必须至少包含一个小写字母。● 该值必须至少包含一个数字。
● 主密码只能包含ASCII字符（ASCII代码33-126），但不包括'（单引号）、"（双引号）、/、\或@。

图3.2 – Amazon Redshift集群数据库配置部分的截图

11. 向下滚动并更改其他配置设置，如图3.3所示：

#### 其他配置

这些配置是可选的，并已定义默认设置以帮助你开始使用集群。现在关闭“使用默认值”以修改这些设置。

#### 网络和安全

虚拟私有云（VPC）
此VPC定义了该集群的虚拟网络环境。选择具有子网组的VPC。列表中仅启用有效的VPC。
默认VPC
vpc-140d146e

ℹ 创建集群后无法更改与此集群关联的VPC。了解更多 ↗ ×

VPC安全组
此VPC安全组定义集群可以在VPC中使用的子网和IP范围。
选择一个或多个安全组
redshift-self ×
sg-059c2134eb1a29141

图3.3 – Amazon Redshift集群其他配置部分的截图

12. 还要更改IAM权限，如图3.4所示：

