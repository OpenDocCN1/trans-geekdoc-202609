
## 输入付款信息

若要使用超出免费层限制的 AWS 服务，您需要提供付款信息。AWS 提供按量付费定价模式，这意味着您只需为所使用的服务付费，无需签订长期合同或进行预付承诺。

## 审阅并确认

请审阅您的账户信息、服务条款和定价详情，然后确认创建您的 AWS 账户。

一旦您的 AWS 账户创建成功，您即可访问 AWS 管理控制台，从而开始配置深度学习环境所需的资源。

# 配置 Amazon EC2 实例

Amazon EC2 提供可扩展的云计算能力，允许您启动称为“实例”的虚拟服务器，以运行您的应用程序和工作负载。配置 EC2 实例是设置深度学习环境的第一步，为训练和推理任务提供所需的计算能力。

在本节中，我们将探讨手动配置方法和使用 AWS CloudFormation 的自动化配置方法。

手动配置 EC2 实例的步骤如下：

- 导航至 EC2 仪表板：登录 AWS 管理控制台，点击“Services”下拉菜单，选择“EC2”，然后从 EC2 服务页面点击“EC2 Dashboard”。
- 启动实例：点击“Launch Instance”按钮，开始实例创建流程。
- 选择 Amazon Machine Image (AMI)：选择一个 AMI 作为您的 EC2 实例的基础。您可以从各种预配置的 AMI 中进行选择，包括针对 TensorFlow 和 PyTorch 等深度学习框架优化的 AMI。
- 选择实例类型：选择最适合您计算需求的实例类型。就本书的项目而言，我们选择了“t2.xlarge”实例类型，它提供 16 GiB 内存和四个 vCPU。虽然该实例不包含 GPU，但它适合运行书中描述的各种演示和实验。然而，对于可能需要加速处理的生产级深度学习任务，您需要一个带有专用 GPU 的实例。
- 配置实例详细信息：自定义实例设置，包括实例数量、网络设置和存储选项。例如，选择一个运行 Ubuntu Server 22.04 LTS（指支持长期支持的 Ubuntu 22.04 操作系统版本）的“t2.xlarge”实例，HVM 虚拟化（硬件虚拟机，提供更好的性能和兼容性），以及 SSD 卷类型（固态硬盘存储，提供更快的磁盘 I/O 性能）。
- 添加存储：指定附加到您 EC2 实例的存储卷。您可以选择多种类型的存储，包括 Amazon Elastic Block Store (EBS) 卷和实例存储卷。
- 配置安全组：为您的 EC2 实例定义安全组，以控制入站和出站流量。确保开放必要的端口，以便与您的深度学习环境进行通信。配置 EC2 实例的安全组涉及定义控制实例入站和出站流量的规则。以下是操作方法：
    - 导航至安全组部分：在启动您的 EC2 实例后，前往 AWS 管理控制台中的 EC2 仪表板。在左侧导航窗格的“Network & Security”部分下，点击“Security Groups”。
    - 创建新的安全组：如果您没有适合您深度学习环境的现有安全组，可以通过点击“Create Security Group”按钮创建一个新安全组。
    - 定义入站规则：在创建或选定的安全组中，定义入站规则以控制流向您的 EC2 实例的传入流量。例如，您可能希望允许 SSH 访问（端口 22）用于远程管理，访问 Jupyter notebook 或 JupyterLab（端口 8888），以及 Apache Airflow 的 Web 界面（默认端口 8080）。您也可以根据需要开放其他端口，以便与其他服务或应用通信。
    - 定义出站规则：同样，定义出站规则以控制从您的 EC2 实例发出的传出流量。默认情况下，允许所有出站流量，但您可以根据具体要求进行限制。
    - 审阅并应用更改：审阅已配置的安全组规则，确保它们满足您的安全性和连接性需求。满意后，点击“Save”或“Apply Changes”按钮以将更改应用到安全组。
    - 将安全组与您的 EC2 实例关联：最后，将新创建或更新的安全组与您的 EC2 实例关联。您可以通过在 EC2 仪表板中选择该实例，点击“Actions”下拉菜单，并选择“Security” ➤ “Change Security Groups”来完成此操作。选择所需的安全组，然后点击“Assign Security Groups”。
- 审阅并启动：审阅实例配置详情并进行必要调整。满意后，点击“Launch”按钮以启动您的 EC2 实例。
- 创建密钥对：如果您尚未创建 SSH 密钥对，系统将提示您创建一个。此密钥对用于通过 SSH 安全连接到您的 EC2 实例。
- 访问您的 EC2 实例：一旦您的 EC2 实例启动，您可以使用 SSH 或其他远程访问方法访问它。首先连接到您的实例，并根据您的深度学习需求对其进行配置。
- 启动和停止您的 EC2 实例：在您的 EC2 实例启动后，您可能需要根据使用情况要求启动或停止它。操作方法如下：
    - 启动实例：在 AWS 管理控制台中导航至 EC2 仪表板。选择您要启动的实例，并从“Actions”下拉菜单中选择“Instance State” ► “Start instance”。
    - 停止实例：同样，要停止实例，请从 EC2 仪表板中选择该实例，并从“Actions”下拉菜单中选择“Instance State” ► “Stop instance”。
    - 注意：如果您在工作完成后未停止实例，将产生费用。请务必在不再需要时停止实例，以避免不必要的成本。

遵循这些步骤，您将成功配置一个 Amazon EC2 实例。

您也可以使用 Amazon CloudFormation 自动执行这些步骤——这是一种允许您使用简单文本文件来定义和配置云基础设施的工具。例如，下面的脚本利用 Amazon CloudFormation 自动化创建一个具有以下配置的 EC2 实例：t2.xlarge 实例类型、40 GB gp3 EBS 卷，以及允许 SSH 访问的安全组：

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: Provision a t2.xlarge EC2 instance with a 40 GB gp3 EBS volume for deep learning tasks

Resources:
  DeepLearningEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.xlarge
      KeyName: instance1keypair.pem
      SubnetId: subnet-04856bd3f80a406e6
      ImageId: ami-05134c8ef96964280
      BlockDeviceMappings:
        - DeviceName: /dev/sda1
          Ebs:
            VolumeSize: 40
            VolumeType: gp3
      SecurityGroupIds:
        - !Ref InstanceSecurityGroup
  InstanceSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Enable SSH access
      VpcId: vpc-09f1a4805e4bd7aa6
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0

Outputs:
  InstanceId:
    Description: Instance ID of the newly created EC2 instance
    Value: !Ref DeepLearningEC2Instance
```

此脚本自动创建具有特定配置的 EC2 实例，包括实例类型、存储卷和安全设置。以下是脚本各部分的详细说明：

- AWSTemplateFormatVersion 和 Description：脚本通过 AWSTemplateFormatVersion 指定 CloudFormation 模板格式的版本，设置为 "2010-09-09"。这表明所使用的 CloudFormation 语法版本。Description 字段提供了模板目的的简要概述。在此情况下，它描述了脚本将配置一个 t2.xlarge EC2 实例，该实例配有 40 GB gp3 EBS 卷，旨在用于深度学习任务。
- Resources 部分：脚本的核心是 Resources 部分，其中定义了 EC2 实例及其相关配置。在此部分中，有两个关键资源：DeepLearningEC2Instance 和 InstanceSecurityGroup。
- DeepLearningEC2Instance：该资源代表 EC2 实例本身。Type 设置为 AWS::EC2::Instance，表示该资源将创建一个 EC2 实例。在 Properties 下配置了多个属性：
    - InstanceType 将实例类型指定为 t2.xlarge，这是一种适用于多种工作负载的通用型实例。

