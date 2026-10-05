
以下代码段落是实现`Suggestion`接口的一个示例。超参数及其值空间在`request`变量中定义。过去的试验及其指标也可以在`request`变量中找到，因此你可以在`GetSuggestions`方法中通过这些输入数据运行算法以计算下一个建议；参见下代码：

```python
class NewAlgorithmService(
    api_pb2_grpc.SuggestionServicer,
    HealthServicer):
    def ValidateAlgorithmSettings(self, request, context):
        # 可选，用于验证
        # 用户定义的算法设置。
        pass
```

定义一个新的算法服务并实现`GetSuggestions`接口

```python
def GetSuggestions(self, request, context):
    search_space = HyperParameterSearchSpace.convert(request.experiment)
```

`Suggestion`函数为每次试验提供超参数。

```python
trials = Trial.convert(request.trials)
```

获取过去的试验

```python
# 实现使用你的算法
# 生成新的当前数量
list_of_assignments = your_logic(search_space,
                                 trials, request_current_number)
```

实现实际算法以提供候选值

```python
return api_pb2.GetSuggestionsResponse()
trials=Assignment.generate(list_of_assignments)
```

## C.5 步骤 2：将算法 Docker 化为 gRPC 服务

一旦我们实现了`Suggestion`接口，我们需要构建一个 gRPC 服务器来暴露此 API，并对其进行 Docker 化，这样 Katib 就可以启动算法并通过发送 gRPC 调用获取超参数了。代码如下：

```python
server = grpc.server(futures.ThreadPoolExecutor(max_workers=10))
service = YourNewAlgorithmService()
api_pb2.add_SuggestionServicer_to_server(service, server)
health_pb2_grpc.addHealthServicer_to_server(service, server)
server.add_insecure_port(DEFAULT_PORT)
print("Listening...")
server.start()
```

## C.5.3 步骤 3：将算法注册到 Katib

最后一步是将新算法注册到 Katib 的启动配置中。在 Katib serve 配置的`suggestion`部分添加一个新条目；示例所示：

```yaml
suggestion: |-
  "tpe": {
    "image": "docker.io/kubeflowkatib/suggestion-hyperopt"
  },
  "random": {
    "image": "docker.io/kubeflowkatib/suggestion-hyperopt"
  },
  "new-algorithm-name":{
    "image": "new algorithm image path"
  }
```
