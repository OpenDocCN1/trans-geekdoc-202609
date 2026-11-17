

## 持续训练

通过 CI/CD 流水线，您可以添加 **持续训练（CT）** 阶段。因此，当运行 CI/CD 流水线时，它还将根据配置设置在最新可用数据上训练模型。

_start.sh_

要在最新数据上训练模型，需要将以下命令添加到 _start.sh_ 文件中：

```
python app/src/prediction_model/train_pipeline.py
```

这将运行 train_pipeline.py 文件并生成训练模型的最新 pickle 文件。该文件将先安装包，然后训练模型，最后运行 FastAPI 应用。

```
1. #!/bin/bash
2.
3. pip install app/src/
4. python app/src/prediction_model/train_pipeline.py
5. python app/main.py
```

## Amazon Elastic Container Registry (ECR)

Amazon Elastic Container Registry (ECR) 是由 AWS 托管的容器镜像仓库服务。它可存储、管理并为私有容器镜像提供安全性。如果需要通过代码或其他服务（例如 **CodeBuild**）来访问这些容器镜像，则需要向指定的服务角色提供容器镜像仓库访问权限。

从服务中进入 Elastic Container Registry：

**服务 | 所有服务 | 容器 | Elastic Container Registry**

创建名为 `mlapp-cicd` 的仓库。默认情况下，仓库的可见性为私有，这意味着访问将由 IAM 管理，并且预定义权限将授予仓库策略。仓库名称应当简洁且有意义，即应基于仓库的内容。名称必须以字母开头，且只能包含小写字母、数字、连字符、下划线、句点和正斜杠。

然后，进入仓库并点击右上角的 **查看推送命令** 按钮。它将显示使用 AWS CLI 从本地机器推送 Docker 容器镜像时需要遵循的推送命令和说明。首先，需要使用弹出窗口中给出的命令登录到 AWS ECR。接下来，在本地机器上使用 docker build 命令构建 Docker 镜像。如果 Docker 镜像已构建，则可以跳过 Docker 构建步骤。然后，使用弹出窗口中给出的命令为 Docker 镜像打标签并将镜像推送到 AWS ECR 仓库。

以下图显示了 `mlapp-cicd` 仓库的推送命令：

![](img/cc4299656808e62a294f1843a1e18e72_361_0.png)

图 13.4：Amazon ECR – 推送命令

> 注：建议在本地机器上安装并配置最新版本的 AWS CLI 和 Docker。

## Docker Hub 速率限制

从 2020 年 11 月 20 日开始，匿名用户和免费用户每 6 小时分别被限制为 100 和 200 次容器镜像拉取请求。超过指定限制后，将抛出包含 ERROR: toomanyrequests: Too Many Requests. 或 You have reached your pull rate limit. 的错误。您可以通过身份验证和升级来提高限制：https://www.docker.com/increase-rate-limits。要提高拉取速率限制，可以将帐户升级为 Docker Pro 或 Team 订阅。Docker Pro 和 Docker Team 帐户每 24 小时可从 Docker Hub 拉取 5,000 次。

为避免此错误，请针对当前场景在 AWS ECR 上创建新仓库。接下来，将 Docker Hub 中的基础 Python 3.7 镜像拉取到本地机器或虚拟机中。然后，将该基础 Python 3.7 镜像推送到新创建的 AWS ECR 仓库。在当前场景中，基础镜像在单独的仓库中维护，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_362_0.png)

图 13.5：Amazon ECR–仓库

在 Dockerfile 中使用此镜像路径，以便在针对 Dockerfile 运行 docker build 命令时，它将从 AWS 拉取基础 Python 3.7 镜像。为此，需要按如下方式更新 Dockerfile：

```
1. # Pull base Python:3.7 image from AWS ECR repository
2. ARG REPO=692601447418.dkr.ecr.us-west-2.amazonaws.com
3.
4. FROM ${REPO}/python:3.7
5.
6. COPY ./start.sh /start.sh
7.
8. RUN chmod +x /start.sh
9.
10. ENV PYTHONPATH "${PYTHONPATH}:app/src/"
11.
```

```
12. COPY . /app

13.

14. RUN chmod +x /app

15.

16. # Exposing the port that uvicorn will run the app on

17. ENV PORT=8000

18. EXPOSE 8000

19.

20. RUN pip install --upgrade pip

21.

22. RUN pip install --no-cache-dir --upgrade -r app/requirements.txt

23.

24. CMD ["./start.sh"]
```

在当前场景中，python:3.7-slim-buster 镜像被构建并打标签为 3.7，然后推送到 AWS ECR 以实现重用。这样，每次都会从 AWS ECR 而不是 Docker Hub 拉取 python:3.7-slim-buster 镜像，以避免任何速率限制错误。

## AWS CodeBuild

CodeBuild 是一种由 AWS 基础设施支持的完全托管型持续集成（CI）服务，可让开发者快速自动化构建、测试和部署容器或软件包。它采用按需或按使用量付费的模式，即根据用户使用的计算资源按分钟计费。

CodeBuild 配置文件类型为 YAML。该文件包含一系列阶段和命令，以执行开发者指定的构建。

*buildspec.yaml*

在这种情况下，buildspec.yaml 文件在 install 阶段中先安装 tox 包。接下来，它将使用 tox 运行测试并在 pre_build 阶段中登录 AWS ECR。然后，buildspec.yaml 文件在 build 阶段构建带 latest 标签的 Docker 容器镜像，并在 post_build 阶段将镜像推送到 AWS ECR 仓库。最后，指定 pytest 报告的详细信息，例如文件、基目录和文件格式。此外，提供要作为项目存储到 S3 存储桶中的文件名。

```
1. version: 0.2
2.
3. phases:
4. install:
5. runtime-versions:
6. python: 3.7
7. commands:
8. - pip install tox
9. pre_build:
10. commands:
11. - echo Running test...
12. - tox
13. - echo Logging into Amazon ECR...
14. - aws --version
15. - aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 692601447418.dkr.ecr.us-west-2.amazonaws.com
16. - REPOSITORY_URI=692601447418.dkr.ecr.us-west-2.amazonaws.com/mlapp-cicd
17. - COMMIT_HASH=$(echo $CODEBUILD_RESOLVED_SOURCE_VERSION | cut -c 1-7)
18. - IMAGE_TAG=${COMMIT_HASH:=latest}
19. build:
20. commands:
21. - echo Build started on `date`
22. - echo Building the Docker image...
23. - docker build -t $REPOSITORY_URI:latest .
24. - docker tag $REPOSITORY_URI:latest $REPOSITORY_URI:$IMAGE_TAG
25. post_build:
26. commands:
27. - echo Build completed on `date`
28. - docker push $REPOSITORY_URI:latest
29. - docker push $REPOSITORY_URI:$IMAGE_TAG
30. - echo Writing container image definitions file...
31. - printf '[{"name":"mlapp-cicd","imageUri":"%s"}]' $REPOSITORY_URI:$IMAGE_TAG > imagedefinitions.json
```

```
33. reports:
34.   pytest_reports:
35.     files:
36.       - Prediction_test_report.xml
37.       - API_test_report.xml
38.     base-directory: pytest_reports/
39.     file-format: JUNITXML
40. artifacts:
41.     files: imagedefinitions.json
```

在前面的文件中，主要使用了三种受支持的构建器镜像。

可以看到，python:3.7 是用于使用 tox 测试代码的公开可用镜像。如果需要从 Docker Hub 使用任何镜像，则只需在单引号中提供镜像名称即可。但是，如果镜像来自其他注册表，则需要在单引号中指定完整的注册表路径。构建阶段的 args 字段接受参数列表，并将它们传递给由 name 字段引用的镜像。

要创建构建，请使用 CodeBuild。在开发者工具中搜索并选择 CodeBuild，然后在构建部分中选择构建项目。点击“创建构建项目”按钮来创建新项目。首先，在“项目配置”下，提供项目名称。

在此情况下，提供了项目名称 mlapp-cicd，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_366_0.png)

图 13.6：CodeBuild–项目配置

接下来，在源部分中，从下拉列表中选择源提供商，并选择后续详细信息，例如仓库和分支。源提供商包含用作构建项目输入源代码的详细信息和代码文件。在当前场景中，选择 AWS CodeCommit 作为源提供商，如下图所示。但是，也可以选择其他源提供商而非 AWS CodeCommit，例如 BitBucket、GitHub 和 S3。
