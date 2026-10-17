

2.  让我们为表字段添加一些元数据。选择 `customer_data` 表，单击 `Edit Schema`，选择 `creditscore` 字段，单击 `Edit` 和 `Add` 以添加列属性，并输入以下内容，其中 `description` 是键，实际文本是值：

    ```
    description: credit score is the FICO score for each customer
    ```

3.  按照相同的步骤，为 `churn_list` 表中的 `exited` 字段添加以下列属性：

    ```
    description: churn flag
    ```

4.  现在我们可以在 Lake Formation 管理控制台中使用元数据进行一些搜索了。尝试在 `Find table by properties` 的文本框中分别输入以下单词，以搜索表并查看返回的结果：

    *   `FICO`

    *   `csv`

    *   `churn flag`

    *   `creditscore`

    *   `customerid`

现在您已找到要查找的表，让我们查询该表并查看实际数据，以了解如何交互式查询数据，这是数据科学家进行数据探索和理解时执行的重要任务。选择要查询的表，并单击 `Actions` 下拉菜单中的 `View data` 按钮。这将带您进入 `Amazon Athena` 屏幕。您应该会看到已创建一个 `Query` 选项卡，并且查询已执行。结果将显示在屏幕底部。如果您收到一条警告消息，指出需要提供输出位置，请选择 `Settings` 选项卡，然后单击 `Manage` 按钮以提供 S3 位置作为输出位置。您可以运行任何其他 SQL 查询来进一步探索数据，例如使用 `customerid` 字段连接 `customer_data` 和 `churn_list` 表：

```
SELECT * FROM "bank_customer_db"."customer_data", " bank_customer_db"."churn_list" where "bank_customer_db"."customer_data"."customerid" = "bank_customer_db"."churn_list"."customerid" ;
```

您现在已了解如何在 Lake Formation 中发现数据，并针对 Lake Formation 数据库和表中的数据运行查询。接下来，让我们使用 Amazon Glue ETL 服务运行一个数据处理作业，以使数据准备好用于 ML 任务。

## 创建 Amazon Glue ETL 作业以处理 ML 数据

`customer_data` 和 `churn_list` 表包含对 ML 有用的特征。但是，需要将它们连接并处理，以便可用于训练 ML 模型。一种选择是让数据科学家下载这些数据集并在 Jupyter 笔记本中对其进行处理以进行模型训练。另一种选择是使用单独的处理引擎处理数据，以便数据科学家可以直接处理已处理的数据。在这里，我们将设置一个 AWS Glue 作业来处理 `customer_data` 和 `churn_list` 表中的数据，并将其转换为可直接用于模型训练的新 ML 特征：

1.  首先，创建一个名为 `MLSA-DataLake-Serving-<your initials>` 的新 S3 存储桶。我们将使用此存储桶来存储 Glue 作业的输出训练数据集。

2.  使用 Lake Formation 控制台，将 `AWSGlueService_Role` 授予 `customer_data` 和 `churn_list` 表的 `Super` 访问权限。我们将使用此角色来运行 Glue 作业。

3.  要开始创建 Glue 作业，请转到 Glue 控制台并单击 Glue 控制台上的 `ETL Jobs` 链接。单击 `Script editor`，然后单击 `Create script` 按钮。

4.  在脚本编辑器屏幕上，将作业名称从 `Untitled job` 更改为 `customer_churn_process`，以便于跟踪。

5.  在 `Job details` 选项卡上，选择 `AWSGlueService_Role` 作为 IAM 角色。在 `Advanced Properties` 下添加一个名为 `target_bucket` 的新 `Job` 参数，并输入目标存储桶的值作为输出文件。

6.  在 `Script tab` 屏幕上，将以下代码块复制到代码部分。确保将代码中的 `default_bucket` 替换为您自己的存储桶。以下代码块首先使用 `customerid` 列作为键连接 `churn_list` 和 `customer_data` 表，然后使用索引转换 `gender` 和 `geo` 列，创建一个仅包含相关列的新 DataFrame，最后使用日期和生成的版本 ID 作为分区将输出文件保存到 S3 位置。代码对目标存储桶和前缀变量使用默认值，并为 S3 位置生成日期分区和版本分区。作业还可以接受这些参数的输入参数。

    以下代码块设置默认配置，例如 `SparkContext` 和默认存储桶：

    ```
    import sys
    from awsglue.utils import getResolvedOptions
    from awsglue.transforms import Join
    from pyspark.context import SparkContext
    from awsglue.context import GlueContext
    from awsglue.job import Job
    import pandas as pd
    from datetime import datetime
    import uuid
    from pyspark.ml.feature import StringIndexer
    glueContext = GlueContext(SparkContext.getOrCreate())
    logger = glueContext.get_logger()
    current_date = datetime.now()
    default_date_partition = f"{current_date.year}-{current_date.month}-{current_date.day}"   
    default_version_id = str(uuid.uuid4())
    default_bucket = "<your default bucket name>"
    default_prefix = "ml-customer-churn"
    target_bucket = ""
    prefix = ""
    day_partition =""
    version_id = ""
    try:
         args = getResolvedOptions(sys.argv,['JOB_NAME','target_bucket','prefix','day_partition','version_id'])
         target_bucket = args['target_bucket']
         prefix = args['prefix']
         day_partition = args['day_partition']
         version_id = args['version_id']
    except:
         logger.error("error occured with getting arguments")
    if target_bucket == "":
         target_bucket = default_bucket
    if prefix == "":
         prefix = default_prefix
    if day_partition == "":
         day_partition = default_date_partition
    if version_id == "":
         version_id = default_version_id
    ```

    以下代码使用 `customerid` 列作为键将 `customer_data` 和 `churn_list` 表连接到一个表中：

    ```
    # catalog: database and table names
    db_name = "bank_customer_db"
    tbl_customer = "customer_data"
    tbl_churn_list = "churn_list"
    # Create dynamic frames from the source tables
    customer = glueContext.create_dynamic_frame.from_catalog(database=db_name, table_name=tbl_customer)
    churn = glueContext.create_dynamic_frame.from_catalog(database=db_name, table_name=tbl_churn_list)
    # Join the frames to create customer churn dataframe
    customer_churn = Join.apply(customer, churn, 'customerid', 'customerid')
    customer_churn.printSchema()
    ```

    以下代码块将多个数据列从字符串标签转换为标签索引，并将最终文件写入 S3 中的输出位置：

    ```
    # ---- Write out the combined file ----
    current_date = datetime.now()
    str_current_date = f"{current_date.year}-{current_date.month}-{current_date.day}"   
    random_version_id = str(uuid.uuid4())
    output_dir = f"s3://{target_bucket}/{prefix}/{day_partition}/{version_id}"
    s_customer_churn = customer_churn.toDF()
    gender_indexer = StringIndexer(inputCol="gender", outputCol="genderindex")
    s_customer_churn = gender_indexer.fit(s_customer_churn).transform(s_customer_churn)
    geo_indexer = StringIndexer(inputCol="geography", outputCol="geographyindex")
    s_customer_churn = geo_indexer.fit(s_customer_churn).transform(s_customer_churn)
    s_customer_churn = s_customer_churn.select('geographyindex', 'estimatedsalary','hascrcard','numofproducts', 'balance', 'age', 'genderindex', 'isactivemember', 'creditscore', 'tenure', 'exited')
    s_customer_churn = s_customer_churn.coalesce(1)
    s_customer_churn.write.option("header","true").format("csv").mode('Overwrite').save(output_dir)
    logger.info("output_dir:" + output_dir)
    ```

