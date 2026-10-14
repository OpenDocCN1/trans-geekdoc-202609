
如果您考虑到机器学习模型更新和持续性能评估的频率，此功能将非常实用。新模型版本的创建可能源于在更新的数据上进行训练、超参数调优（例如使用 Amazon SageMaker AI AMT）、改进特征选择，或使用更好的实例和推理容器。您可以利用生产变体来比较模型，并选择性能最佳的候选模型来响应推理请求。

借助 Amazon SageMaker AI 多变体端点，您可以通过为每个变体提供流量分配，将端点调用请求分发到多个生产变体；或者您也可以为每个请求直接调用特定变体。在本节中，我们将探讨这些部署和测试机器学习模型的方法。

## 蓝绿部署

蓝绿部署是一种降低部署新模型版本相关风险和停机时间的策略。在 Amazon SageMaker AI 中，可以通过利用您刚学到的生产变体概念来有效实施此方法，从而实现不同模型版本或配置之间的无缝流量切换。通过精心控制流量流向，您可以确保用户体验到的中断最小化，同时验证新模型版本的性能和稳定性。

在深入细节之前，让我们先统一一下考试所需了解的几个术语，它们构成了该策略的基础。在蓝绿部署策略中，*蓝色车队* 是指现有模型版本正在为实时流量提供服务的计算基础设施。而 *绿色车队* 则是托管您想要部署的新模型版本的计算基础设施。目标是以受控方式将流量从蓝色车队转移到绿色车队，确保新模型在完全替换旧模型之前，在真实环境下表现良好。通过使用这种方法，您可以最大限度地减少停机时间，并降低新部署引入问题的风险。

在完全过渡到新模型之前，新模型版本会经过严格的测试和验证，以确保其性能和可靠性。在此期间——称为 *烘焙期*——新模型（部署在绿色车队上）在为实时流量提供服务时会受到监控。这将确保其性能符合预期，并满足您建立的性能指标。一旦绿色车队开始接收实时流量，烘焙期便开始。为实现这一点，必须正确配置 CloudWatch 警报，以持续监控关键性能指标和新模型的行为。烘焙期允许您尽早发现问题，并在将更多流量导向新模型之前加以解决。这一额外的验证步骤对于维护服务质量和最大限度地降低中断风险至关重要。

术语 *流量切换模式* 是指您希望 Amazon SageMaker AI 端点在蓝色车队和绿色车队之间分发推理请求时所使用的入站流量模式。

最后，*自动回滚* 是指 Amazon SageMaker AI 用于监控新版本模型在（托管在）绿色车队上的（容器）性能的 Amazon CloudWatch 警报。

在接下来的三节中，将解释考试所需了解的三种流量切换模式：即 All At Once（一次性）、Canary（金丝雀）和 Linear（线性）。

### All At Once（一次性）

实施 *All At Once* 流量切换时，Amazon SageMaker AI 会将 100% 的流量导向新车队（绿色车队）。一旦绿色车队开始服务流量，烘焙期便开始。此期间是一个预定的时间间隔，在此期间 Amazon CloudWatch 警报会监控绿色车队的性能。如果在此期间未触发任何警报，Amazon SageMaker AI 将移除旧车队（蓝色车队）。但是，如果激活了任何警报，将启动自动回滚，将 100% 的流量重新导回蓝色车队。

[图 6.7](#c006.xhtml#c06-fig-7) 展示了 All At Once 流量切换模式。

![图 6.7 采用 All At Once 流量切换模式的蓝绿部署。](images/c06f007.png)

[图 6.7](#c006.xhtml#rc06-fig-7) 采用 All At Once 流量切换模式的蓝绿部署。

在 [图 6.7](#c006.xhtml#c06-fig-7) 中，我们要部署名为 `Model_v2` 的模型新版本。起初，当前版本模型 `Model_v1` 正在为实时生产流量提供服务。入站流量由 Amazon SageMaker AI 客户端发起，该客户端使用 `invoke_endpoint` boto3 API 从蓝色车队中托管的 `Model_v1` 获取推理结果。要了解有关此 API 的更多信息，请访问 `https://boto3.amazonaws.com/v1/documentation/api/1.35.9/reference/services/sagemaker-runtime/client/invoke_endpoint.html`。

正如您在 [图 6.7](#c006.xhtml#c06-fig-7) 中所见，该端点具有一个包含两个生产变体的配置，第一个用于 `Model_v1`，第二个用于 `Model_v2`。这是流程中的蓝绿创建步骤。

然后我们通过将所有实时流量重定向到 `Model_v2` 来更改流量模式。这就是烘焙期开始的时候。为实现此步骤，我们使用带有以下代码片段的 `update_endpoint` boto3 API：

```
import boto3
client = boto3.client("sagemaker")
    
response = client.update_endpoint(
  EndpointName="<your-endpoint-name>",
  EndpointConfigName="<your-config-name>",
  DeploymentConfig={
      "BlueGreenUpdatePolicy": {
          "TrafficRoutingConfiguration": {
              "Type": "ALL_AT_ONCE"
          },
          "TerminationWaitInSeconds": 600,
          "MaximumExecutionTimeoutInSeconds": 1800
      },
      "AutoRollbackConfiguration": {
          "Alarms": [
              {
                  "AlarmName": "<your-cw-alarm>"
              },
          ]
      }
  }
)
```

在该片段中，参数 `MaximumExecutionTimeoutInSeconds` 设置部署在超时前可以运行的最长时间（本例中为 30 分钟）。参数 `TerminationWaitInSeconds` 告知 Amazon SageMaker AI 在绿色车队完全激活后，等待指定时间（以秒为单位），然后再终止蓝色车队中的实例。在本例中，Amazon SageMaker AI 在最终烘焙期结束后等待 10 分钟，然后终止蓝色车队。

有关 `update_endpoint` API 调用的详细语法，请访问 `https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sagemaker/client/update_endpoint.html`。

`update_endpoint` API 调用的效果是 [图 6.7](#c006.xhtml#c06-fig-7) 中间所示的新端点配置。

在最理想的情况下，烘焙期间未触发任何警报，从而导致蓝色车队终止。否则，将启动自动回滚，100% 的流量将切回蓝色车队。

### Canary（金丝雀）

在 Amazon SageMaker AI 的金丝雀部署中，与 All At Once 方法相比，流量切换更加渐进。最初，一小部分被认为可行的流量会被导向新车队（绿色车队），而大部分流量继续导向旧车队（蓝色车队）。这个初始阶段称为“金丝雀测试”。如果新车队在金丝雀测试期间表现良好，且未触发任何 Amazon CloudWatch 警报，则流量会在后续步骤中逐渐增加到新车队，直到达到 100%。这种方法允许在生产环境中更密切地监控新版本，并通过让一小部分用户尽早发现潜在问题，降低引入问题的风险。

以编程方式实施金丝雀部署的方法与 All At Once 类似，如以下代码片段所示：
