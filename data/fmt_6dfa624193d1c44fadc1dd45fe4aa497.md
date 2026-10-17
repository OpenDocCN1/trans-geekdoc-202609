
# DM 返回新创建数据集的元数据

```json
{
  "dataset_id": "1",          < 数据集标识符
  "name": "tweet_emotion",    < 数据集名称
  "dataset_type": "TEXT_INTENT",
  "last_updated_at": "2022-03-25T01:32:57.493162Z",
}
```

数据集类型：

```json
"commits": {
  "dataset_id": "1",
  "commit_id": "1",
  "created_at": "2022-03-25T01:32:38.919357Z",
  "commit_message": "Initial commit",
  "path": "dataset/1/commit/1",
  "statistics": {
    "numExamples": "2963",
    "numLabels": "3"
  }
}
```

数据集元数据将在第 2 章中讨论。现在，我们可以忽略数据集 JSON 的大部分属性，只关注`dataset_id`属性。数据集 ID 是数据集的唯一标识符；你需要在第 3 步中将此 ID 传递给训练服务。一旦数据集准备就绪，Feng 就通知 Ivan 使用`dataset_id="1"`开始模型训练。

第 3 步是模型训练。运行`scripts/lab-003-first-training.sh`（http://mng.bz/vnra）。

Ivan（第一位科学家）构建意图分类代码（http://mng.bz/jnka 中的`training-code/test-classification`）并将其打包成 Docker 镜像（http://mng.bz/WA5g）。接下来，Ivan 向训练服务提交请求以创建一个模型作业。在训练请求中，他指定了训练时使用哪个数据集（数据集 ID）和训练算法（Docker 镜像名称）。

注意：在本实验中，我们使用硬编码的数据集 ID "1"。要测试其他数据集，请随时在训练请求中使用任何其他数据集 ID。

一旦训练服务接收到请求，它将启动一个 Docker 容器运行 Ivan 提供的意图分类代码。在我们的演示中，Docker 镜像为`orca3/intent-classification`（http://mng.bz/WA5g）。示例 gRPC 请求请参见列表 A.3。请运行实验脚本（http://mg.bz/9l6 中的`scripts/lab-003-first-training.sh`）来启动模型训练，该脚本会设置依赖和参数。

- 列表 A.3 向训练服务提交训练作业

```bash
# 向训练服务发送 gRPC 请求以启动模型训练。
function start_training() {
  grpcurl -plaintext -d '{
    "algorithm": "intent-classification",
    "dataset_id": "1",
    "name": "test",
    "data_version_hash": "v1",
    "output_model_name": "twitter-model",
    "parameters": {
      "LR": 0.001,
      "EPOCHS": 15,
      "BATCH_SIZE": 64,
      "FC_SIZE": 128
    }
  }' localhost:6003 TrainingService/Train
}
```

![](img/9dbecdac1b6cad2e40ace2d4b22.png)

一旦训练作业开始，训练服务将持续监控执行状态并返回一个作业 ID 用于追踪。有了作业 ID，可以查询训练执行状态。参考列表 A.4 的示例查询：

```bash
# 从训练服务查询作业状态
grpcurl -plaintext -d '{"job_id": "1"}' localhost:6003 TrainingService/GetStatus
```

```bash
# 从元数据存储查询状态
grpcurl -plaintext -d '{"job_id": "1"}' localhost:6003 MetadataStore/GetStatus
```

训练服务会返回执行状态，如下：

```
job 1 正在运行
job 1 正在运行
job 1 正在运行
```

元数据存储会返回执行状态：

```
job 1 正在运行
job 1 正在运行
job 1 正在运行
```
