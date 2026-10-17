
## 将您的 ML 模型投入运行

将机器学习（ML）模型投入运行是指将模型从开发阶段过渡到生产环境的过程，在那里它可以提供实时预测并为业务带来具体价值。这一关键步骤确保模型的能力能够有效地被利用以解决现实世界的问题。以下是详细的过程：

## 模型开发

在投入运行之前，ML 模型会经历以下几个开发阶段：

数据收集和预处理：收集并清理数据，确保为模型提供高质量的输入。

模型训练：使用算法在处理后的数据上训练模型。

评估：使用多种指标评估模型性能，并进行微调以提高准确性。

## 过渡到生产环境

从开发环境（通常是受控的、有限的环境）过渡到生产环境（实时、运行的环境）涉及以下关键步骤：

### 模型部署

环境配置：配置必要的基础设施，如服务器或云服务，以托管模型。

集成：将模型集成到现有系统和应用程序中。这可能包括设置 API 或将模型嵌入软件解决方案。

可扩展性：确保基础设施能够处理预期负载并按需扩展。这包括负载均衡和自动扩展机制。

### 监控和维护

性能监控：持续跟踪模型性能，确保其达到要求的标准。这包括设置仪表盘和告警系统。

错误处理：实施机制，以优雅地处理预测错误和系统故障。

再培训：定期用新数据更新模型，以保持和提高其准确性。这可能涉及自动化再培训管道。

## 创造价值

将 ML 模型投入运行的最终目标是创造价值。这通过以下方式实现：

改进决策：提供可操作的洞察和预测，帮助做出明智的决策。

自动化：简化以前手动执行的流程，提高效率并降低成本。

增强客户体验：为客户提供个性化和及时的服务或产品。

## 挑战和考虑因素

投入运行 ML 模型也面临挑战和考虑因素：

安全性：确保模型及其使用的数据免受未经授权的访问和 breaches。

合规性：遵守关于数据使用和隐私的监管要求和行业标准。

成本管理：在模型生成的价值与基础设施和维护成本之间取得平衡。

## 介绍 Python 中的 API

### 什么是 API？

API（Application Programming Interface，应用编程接口）是构建和交互软件应用程序的规则和协议的集合。API 定义了开发人员可以用于与外部系统或软件组件交互的方法和数据结构。它们使不同软件系统能够通信，实现数据交换和功能共享。

### 为什么使用 API？

API 之所以被广泛使用，有以下几个原因：

集成：API 允许不同的应用和服务协同工作。例如，在电子商务网站中集成支付网关。

自动化：通过连接各种工具和服务来自动化任务。

数据访问：从外部来源获取数据，如天气数据、股票价格或社交媒体动态。

可扩展性：API 通过解耦客户端和服务器，实现可独立演变的可扩展性。

## 介绍使用 Flask 创建 API

`Flask` 是一种轻量级的 WSGI Web 应用框架，设计时注重简洁和灵活性，使其成为构建 Web API 的 excellent 选择。以下是开始使用 Flask 创建 API 的方法。

### 设置 Flask

首先，您需要安装 Flask。可以使用 `pip` 进行安装：

### 创建简单的 Flask API

让我们从创建一个基本的 API 开始，该 API 处理 GET 请求。

#### 逐步指南

导入 Flask：导入 Flask 库中所需的组件。

初始化 Flask 应用：创建 `Flask` 类的实例。

定义路由：使用装饰器定义 API 将响应的路由。

运行应用：运行 Flask 应用。

Figure 5-1 显示了一个插图。

![](img/image_rsrc57D.jpg)

Figure 5-1.

## 代码解释

![](img/image_rsrc57E.jpg)

导入库：

`Flask`：用于创建 Web 应用的主类。

`jsonify`：用于将 Python 字典转换为 JSON 响应。

`request`：用于包含 HTTP 请求的数据（例如 POST 请求中发送的数据）。

## 创建 Flask 应用实例

![](img/image_rsrc57F.jpg)

这一行创建了 `Flask` 类的实例。传递的 `__name__` 变量有助于 Flask 确定应用的根路径。

### 定义路由

定义 `/hello` 路由：

![](img/image_rsrc57G.jpg)

`@app.route('/hello', methods=['GET'])`：此装饰器将 URL `/hello` 与 `hello` 函数绑定，并指定该路由响应 GET 请求。

`def hello`：在客户端向 `/hello` 发出 GET 请求时执行的函数。

`return jsonify({'message': 'Hello, World!'})`：函数返回一个包含消息 "Hello, World!" 的 JSON 响应。

定义 `/greet` 路由：

![](img/image_rsrc57H.jpg)

`@app.route('/greet', methods=['POST'])`：此装饰器将 URL `/greet` 与 `greet` 函数绑定，并指定该路由响应 POST 请求。

`def greet`：在客户端向 `/greet` 发出 POST 请求时执行的函数。

`data = request.get_json()`：获取 POST 请求体中的 JSON 数据。

`name = data.get('name')`：从 JSON 数据中提取 'name' 键关联的值。

`greeting = f"Hello, {name}"`：使用提取的 name 创建问候消息。

`return jsonify({'message': greeting})`：返回一个包含个性化问候消息的 JSON 响应。

## 运行应用

![](img/image_rsrc57J.jpg)

这段代码确保只有当脚本直接运行时（而不是作为模块导入）才运行 Flask 应用。

`app.run(debug=True)`：启动 Flask 开发服务器并启用调试模式。调试模式提供详细的错误消息并当代码更改时自动重新加载服务器。

### 这些部分是如何协同工作的

GET 请求到 `/hello`：

当客户端（例如 Web 浏览器或 Postman 等工具）向 `http://localhost:5000/hello` 发出 GET 请求时，`hello` 函数被调用。

服务器响应一个 JSON 对象：`{"message": "Hello, World!"}` 。

POST 请求到 `/greet`：

当客户端向 `http://localhost:5000/greet` 发送包含 JSON 体 `{"name": "Alice"}` 的 POST 请求时，`greet` 函数被调用。

`greet` 函数处理传入的 JSON 数据，提取 'name' 值，并构建个性化问候语。

服务器响应一个 JSON 对象：`{"message": "Hello, Alice"}` 。

## 测试 API

使用 Postman：

GET 请求：输入 `http://localhost:5000/hello` 并点击“发送”。

POST 请求：输入 `http://localhost:5000/greet`，选择“POST”，将 Body 设置为原始 JSON，并输入 `{"name": "Alice"}`。然后点击“发送”。

图 5-2 和图 5-3 展示了 Postman 中的操作。

![](img/image_rsrc57K.jpg)

图 5-2。

![](img/image_rsrc57M.jpg)

图 5-3。

这个 Flask 示例展示了如何设置一个简单的 Web API，能够处理 GET 和 POST 请求。`/hello` 路由返回静态消息，而 `/greet` 路由根据提供的 JSON 数据动态生成个性化问候语。Flask 的简洁和灵活使其成为快速高效构建 Web API 的理想选择。

## 将机器学习模型转换为 API

训练完成后，可以使用 `Pickle` 库将模型序列化以保存其状态，后续加载该模型用于进行预测。`Pickle` 是 Python 中用于序列化和反序列化 Python 对象结构的模块，也称为序列化或展平。序列化是将 Python 对象转换为字节流的过程，以便保存到文件或数据库，或通过网络传输。反序列化则是将字节流转换回 Python 对象的逆过程。

### 如何使用 Pickle

以下示例演示如何使用 Pickle 进行序列化和反序列化：

### 示例：序列化和反序列化 Python 对象

**序列化（Pickling）对象**：

![](img/image_rsrc57N.jpg)

在本例中，字典 `data` 被序列化并保存到名为 `data.pkl` 的文件中。该文件可以保存在您应用程序的目录或任何 API 可访问的位置。

**反序列化（Unpickling）对象**：

![](img/image_rsrc57P.jpg)此代码从 `data.pkl` 读取序列化数据并反序列化为 Python 字典。

以下是输出结果：

![](img/image_rsrc57R.jpg)

## 为 pickle `data.pkl` 文件创建 API

![](img/image_rsrc57S.jpg)

在本 Flask 应用中：

我们定义了一个 `/deserialize` 路由，接受 POST 请求。

在路由函数内部，从 POST 请求的 JSON 负载中提取序列化对象的文件名。

尝试使用 `pickle.load()` 从指定文件中反序列化对象。

如果反序列化成功，返回包含反序列化对象的 JSON 响应。

如果文件未找到或在反序列化过程中发生其他错误，返回错误响应。

为测试该 API 端点，可以向 `/deserialize` 发送 POST 请求，并在 JSON 负载中包含序列化对象的文件名：

![](img/image_rsrc57T.jpg)

## 将第 4 章的无监督学习模型转换为 API

我们将按照以下步骤将第 4 章中的机器学习模型转换为 API：

**将机器学习模型转换为 API**

图 5-4 展示了如何导出我们的机器学习模型（本例中为第 4 章的 `kmeans`），并将其序列化为名为 `model.pkl` 的 pickle 文件。

![](img/image_rsrc57U.jpg)

图 5-4。

### 代码说明

`import pickle` 语句导入 `pickle` 模块，该模块提供序列化和反序列化 Python 对象的函数。

`open('model.pkl', 'wb')` 语句以二进制写入模式打开名为 `model.pkl` 的文件，该文件用于保存序列化对象。

`with` 语句作为上下文管理器，自动在代码块执行完毕后关闭文件。

在 `with` 块内部，`pickle.dump(kmeans, f)` 使用 `pickle.dump()` 函数将 `kmeans` 对象序列化并写入文件 `f`。该函数接受两个参数：要序列化的对象 (`kmeans`) 和序列化数据写入的文件对象 (`f`)。

执行完此代码后，`kmeans` 对象将被序列化并保存到 `model.pkl` 文件中，随后可以使用 `pickle.load()` 加载。

接下来，将 `model.pkl` 文件复制到您首选的目录并引用它。在我的情况，模型被放在应用程序根目录中，如图 5-5 所示。

![](img/image_rsrc57V.jpg)

图 5-5。

以下是完整代码：

![](img/image_rsrc57W.jpg)

### 代码说明

此代码定义了一个 Flask API，包含单个端点 `/api/custype`，接受 POST 请求。我们逐步解析代码：

**导入**：

`from flask import Flask, jsonify, request`：导入 Flask 框架及处理 JSON 响应和 HTTP 请求的必要模块。

`import pickle`：导入 `pickle` 模块用于序列化和反序列化 Python 对象。

`import numpy as np`：导入 `numpy` 库，用于 Python 中的数值计算。

**Flask 应用初始化**：

`app = Flask(__name__)`：创建 Flask 应用实例。

**API 端点 `/api/custype`**：

`@app.route('/api/custype', methods=['POST'])`：装饰器将 `Custype()` 函数设为 `/api/custype` 端点的 POST 请求处理函数。

`def Custype():`：定义 `Custype()` 函数以处理 `/api/custype` 端点的请求。

**函数内部**：

`data = request.get_json():` 从请求负载中获取 JSON 数据。

`Annual_Income = data.get('Annual_Income') and Spending_Score = data.get('Spending_Score'):` 从 JSON 数据中提取 `'Annual_Income'` 和 `'Spending_Score'` 的值。

`filename = 'model.pkl'`：指定序列化模型的文件名。

**反序列化模型**：

使用 `pickle.load(f)` 从文件 `'model.pkl'` 中反序列化模型。

**进行预测**：

使用加载的模型对提供的 `'Annual_Income'` 和 `'Spending_Score'` 值进行预测。

**构建响应**：

构造包含预测结果的消息，并以 JSON 响应返回。

**异常处理**：

`try-except` 块捕获在预测过程中发生的任何异常，并返回相应的错误响应。

**运行 Flask 应用**：

`if __name__ == '__main__':` 检查脚本是否直接运行。

`app.run(debug=True)`：启动 Flask 开发服务器，开启调试模式。

## 预测消息说明

JSON 响应中返回的预测消息指示根据年收入和消费评分预测的客户所属的聚类。消息包含客户的年收入、消费评分以及所属的聚类编号。

总体而言，这个 Flask API 端点演示了如何通过 POST 请求传入数据，使用已训练的机器学习模型进行预测，并以 JSON 响应的形式返回预测结果。

## 使用 Postman 测试

图 5-6 展示了在本地系统上使用 Postman 测试本地 API 的情况。

![](img/image_rsrc57X.jpg)

图 5-6。

结果解释如第 4 章中对聚类结果的解释，这意味着客户具有高平均年收入，并参与适度的交易活动。

## 部署

该 API 可部署在支持 Python 的各种平台，如 Azure、AWS、PythonAnywhere 和 Aiven。这些平台提供强大的托管服务，可用于部署和管理您的 API。部署后，可将端点 URL 分享给前端开发团队，以便集成到应用程序中。

这些平台中的许多在初始阶段提供免费托管选项，之后通常会收取信用卡费用。在选择托管提供商时，了解条款和价格细节非常重要，以便有效管理成本并做出明智的托管决策。这将帮助您高效地管理费用并根据需求选择合适的托管方案。

我们选择使用 Pythonanywhere（`https://www.pythonanywhere.com/`）作为本应用的托管平台，因为其稳健性和灵活性，使其非常适合我们的测试部署。Aiven 提供可靠的应用部署环境，并支持 Python 以及必要库的安装。然而，您可以自由选择任何支持 Python 并能够安装所需库或提供管理依赖关系的环境的部署平台。这种灵活性使您能够根据项目需求和运营偏好选择最合适的平台。

## Step 1: Access PythonAnywhere

在浏览器中访问 `https://www.pythonanywhere.com/` 以访问该平台。图 5-7 展示了 PythonAnywhere 的登陆页面。点击 **plans & pricing** 并点击“Create a Beginner account”按钮，如图 5-8 所示。

![](img/image_rsrc57Y.jpg)Figure 5-7.

## Step 2: Start the onboarding process

点击图 5-8 中所示的按钮，启动入职流程。完成入职后，继续登录。

![](img/image_rsrc57Z.jpg)Figure 5-8.

## Step 3: Login form

图 5-9 展示了登录表单，您需要在此输入登录信息以进入仪表盘。

![](img/image_rsrc580.jpg)Figure 5-9.

## Step 4: Navigate to Files

从仪表盘点击 **Files** 链接，如图 5-10 所示。

![](img/image_rsrc581.jpg)Figure 5-10.

## Step 5: Create a directory

为您的应用文件命名目录，点击 **New directory** 按钮创建它，如图 5-11 所示。

![](img/image_rsrc582.jpg)Figure 5-11.

## Step 6: Upload files

进入您创建的 **mysite** 目录。点击 **Upload a file** 按钮，选择 `app.py` 并提交。重复此过程上传 `model.pkl`。上传的文件将如图 5-12 所示。

![](img/image_rsrc583.jpg)Figure 5-12.

## Step 7: Access Web setup

点击 **Web** 链接，如图 5-13 所示。这将引导您进入 API 或应用的设置区域。
