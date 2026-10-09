

- 在环境详情页面中，您将看到一个打开 Airflow UI 的选项。单击“Open Airflow UI”按钮，即可进入 Apache Airflow 网页界面。

- 监控 DAG：
  - DAG 视图：在 Airflow UI 中，您可以查看所有 DAG 的列表。此视图允许您检查每个 DAG 的状态、最近一次运行情况和调度计划。
  - 图形视图：点击特定的 DAG 可查看图形视图，该视图展示了 DAG 的结构以及每个任务的状态。
  - 树状视图：树状视图提供了随时间变化的 DAG 运行和任务状态的分层视图。
  - 甘特图：甘特图视图有助于可视化 DAG 中每个任务随时间变化的持续时间。
  - 代码视图：您还可以查看 DAG 的代码，以确保逻辑正确实现。
  - 日志：为了进行详细的调试和监控，您可以访问每个任务实例的日志，以查看输出以及在执行过程中发生的任何错误。

Amazon CloudWatch 通过跟踪各种指标和日志、创建仪表板以及设置警报来提供强大的监控功能，以便在发生性能问题、故障或其他关键事件时通知您。通过结合使用 MWAA 和 CloudWatch，您可以确保您的深度学习模型持续提供价值，同时保持高性能、可靠性和合规性的标准。

CloudWatch 提供了几项功能，可以帮助您跟踪 MWAA 环境、DAG 运行以及底层基础设施。以下是您可以如何使用 CloudWatch 来实现这一目的：

- 指标收集：
  - MWAA 指标：MWAA 会自动将指标发布到 CloudWatch。这些指标包括有关环境健康状况的信息，例如调度器、工作程序和网络服务器的状态，以及任务级和 DAG 级指标。
  - 自定义指标：您还可以使用 boto3 库将自定义指标从您的 DAG 或任务推送到 CloudWatch。例如，您可以发布诸如模型推理时间、准确率分数或资源使用率等指标。

- 日志监控：
  - 任务日志：可以将 Airflow 任务日志发送到 CloudWatch 日志。这允许您查看和搜索单个任务的日志，这对调试和监控模型的性能非常有用。
  - MWAA 环境日志：MWAA 还可以将与环境本身相关的日志发送到 CloudWatch 日志。这包括来自调度器、网络服务器和其他组件的日志。

- 警报和通知：
  - CloudWatch 警报：您可以基于 CloudWatch 指标设置警报，以便在特定事件发生时收到通知，例如任务高故障率、延迟增加或其他性能问题。
  - Amazon SNS：使用 Amazon Simple Notification Service (SNS) 在触发警报时接收通知（电子邮件、短信等）。

- 仪表板：
  - CloudWatch 仪表板：创建自定义仪表板以可视化您的 MWAA 环境和模型的指标和日志。这可以包括显示任务成功/失败率、执行时间、资源使用率和其他相关指标的图表。

## 摘要

在本书的最后这一章中，我们深入探讨了部署和监控深度学习模型的过程。使用 Amazon MWAA 简化了在云中设置、管理和扩展 Apache Airflow 环境的过程，消除了对手动基础设施管理的需求。

我们研究了部署过程中的步骤，包括设置环境、开发 DAG、上传到 S3、配置 MWAA 环境以及触发和监控 DAG 执行。本章重点关注两个监控工具：Amazon MWAA 控制台和 Amazon CloudWatch。我们还强调了监控深度学习模型的重要性，以确保其随时间保持性能和准确性，维持运营效率，遵守合规性和治理标准，并增强安全性。

## 索引

- **A**
  - 访问控制列表 (ACLs)，73
  - 准确率，29, 385-387, 395, 461, 465, 545
  - 自适应查询执行 (AQE)，116, 145, 146, 210
  - Airflow
    - Docker，95-100
    - 在 EC2 上，87
    - MWAA，87
    - 独立安装
      - 访问 airflow UI，93-95
      - 激活您的环境，87
      - 管理员用户，91, 92
      - 配置和设置，90, 91
      - 数据库，88
      - 安装和配置 PostgreSQL，88
      - 抽象层，87
      - 端口 8080，94
      - PostgreSQL shell，88, 89
      - PostgreSQL 支持，88
      - 调度器，92
      - tmux/screen，92
    - 更新和安装依赖项，87
    - web 服务器，92, 94
  - Airflow web 服务器，38, 92, 94, 95, 99
  - Amazon CloudFormation，28, 64
  - Amazon CloudWatch，704, 736-738
  - Amazon Elastic Block Store (EBS)，61
  - Amazon Machine Images (AMIs)，26, 61, 67
  - Amazon S3，2, 3, 70-75, 126, 184, 729, 731
  - Amazon S3 存储桶，78, 162, 164, 183, 381, 719
  - AmazonS3FullAccess 策略，107
  - Amazon Simple Storage Service (S3)
    - 配置存储桶属性，71, 72
    - 创建存储桶，71
    - IAM 角色，74, 75
    - 导航到 S3 仪表板，71
    - 可靠且具成本效益，70
    - 上传数据，74
  - Amazon Web Services (AWS)，1, 2, 56, 361, 703, 731
  - 一个 `__init__` 方法，118
  - Apache Airflow，30, 56
    - 活跃社区，30
    - 优势，48, 49
    - DAG
      - 配置，34, 36, 37
      - 默认参数，43
      - 定义，44
      - 导入语句，40
      - 提供上下文，45
      - 运行，37–39
      - 任务依赖项，45
      - 任务函数，41–43
      - 任务操作符，45
    - 深度学习，703
    - 部署选项，39
    - 开发，30
    - 糖尿病预测（参见 糖尿病预测）
    - Docker 容器化设置，39
    - 功能，30
    - MWAA，39
    - 替换，main() 函数，47, 48
    - 可扩展的数据处理管道，490, 584, 703
    - 独立 Airflow，39
    - 特斯拉股价预测（参见 特斯拉股价预测）
    - UI，46, 47
  - 应用程序接口 (API)，9, 85
  - AWS 账户
    - AWS 网站，59
    - 构建和部署，59
    - 创建一个新的 AWS 账户，59
    - 付款信息，60
    - 提供账户信息，59
    - 审查和确认，60
    - 支持计划，59
    - 验证您的身份，59
  - AWS CLI，4–6, 59, 75, 219, 434, 705
  - AWS CloudFormation，60
  - AWS 管理控制台，58, 62, 99, 105, 106, 705–708, 735
  - AWS Secrets Manager，74

- **B**
  - 反向传播，18, 236, 237, 373, 498
  - 平衡模型复杂度，390, 463
  - 基线模型，586
    - 调整超参数，602
    - convert_to_numpy 方法，591, 637
    - create_and_train_model 方法，592, 639
    - 当前性能水平，602
    - 数据增强，602
    - evaluate_model 方法，594, 640
    - 库，587
    - 日志记录，587
    - main 函数，596, 641
    - matplotlib.pyplot，587
    - 模型损失，601
    - 模型简化，602
    - numpy，587
    - 过拟合，602
    - 性能，验证集，602
    - predict_and_evaluate 方法，595, 641
    - preprocess_data 方法，588, 636
    - pyspark.ml.feature，587
    - pyspark.sql，587
    - 正则化，587, 603
    - 审查平台期，602
    - sklearn.metrics，587
    - tensorflow，587
    - 测试损失，599, 642
    - 训练损失图，601
    - TSLARegressor 类，587, 588, 635
  - BCEWithLogitsLoss 函数，384
  - 黑盒，214, 273, 353
  - BlockDeviceMappings，67
  - Boto3，86, 117, 151, 325, 361
  - boto3.client('s3') 方法，126
  - 广播连接，116, 210
  - 存储桶策略，73
  - 内置日志模块，362

- **C**
  - cache() 方法，327
  - 缓存，10, 116, 144, 210, 327, 567
  - calculate_average_price 函数，34, 45, 47
  - calculate_average_price(taco_df) 函数，34
  - calculate_descriptive_statistics 方法，121, 132
  - calculate_feature_target_correlation 方法()，338–340, 344, 352
  - CalledProcessError 异常，220
  - check_for_null_values 方法，117, 123, 135
  - 分类，321
  - 云计算解决方案，214
  - 命令行界面 (CLI)，4, 39, 48, 221
  - 统一计算设备架构 (CUDA)，85
  - 混淆矩阵，29, 30, 378, 387
  - convert_to_numpy() 方法，279, 287, 299, 591, 637
  - convert_to_tensor() 函数，160, 162
  - 卷积神经网络 (CNNs)，19
  - copy_and_print_data()，217, 218, 221
  - copy_file_from_s3() 函数，128, 151, 175, 183, 186, 340–343, 382
  - count_outcome 方法，334, 335, 352
  - count_zeros() 方法，330, 331, 347
  - create_and_train_model() 方法，281, 288, 289, 299, 592, 600, 603, 607, 639

