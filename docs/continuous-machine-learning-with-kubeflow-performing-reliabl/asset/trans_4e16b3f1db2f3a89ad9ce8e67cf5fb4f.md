
```
"image": "$image"
}
}
}
}
}
}"""
kfservingjson = kfserving_template.substitute({'name':
str(serving_name),
'namespace': str(serving_namespace),
'image': str(image)})
kfservingdeployment = json.loads(kfservingjson)
serve = dsl.ResourceOp(
name="serve",k8s_resource=kfservingdeployment,
action="apply",success_condition="status.url")
serve.after(evaluation_model_step)
```

```
if __name__ == '__main__':
import kfp.compiler as compiler
pipeline_func = brain_tensorflow_pipeline
pipeline_filename = pipeline_func.__name__ + '.pipeline.yaml'
compiler.Compiler().compile(pipeline_func,pipeline_filename)
```

因此，让我们按如下方式拆分流水线代码：

预计流水线应包含一个 @dsl.pipeline 装饰器以提供有关流水线的元数据。

流水线在 brain_tensorflow_pipeline 函数中定义。它包含多个参数，这些参数在创建新的 Run 时会在 Kubeflow Pipelines UI 中公开。尽管以字符串形式传递，这些参数的类型为

每个单独的块定义一个组件，如‘train’、‘evaluation’等。组件由一个带有指定容器路径和名称的 **kfp.dsl.ContainerOp** 对象组成。使用的容器镜像定义为我们已创建的 Dockerfile。

在定义 train 组件之后，我们还为训练脚本设置了一些环境变量。

脚本底部是 main 函数。它用于在运行脚本时编译流水线；然后 **.after** 方法将依次触发流水线。

接下来，我们将创建一个实验；在该实验下，我们可以创建流水线的多次运行。以下代码用于创建实验：

```
EXPERIMENT_NAME = 'Brain_experiment'
client = kfp.Client()
try:
experiment =
client.get_experiment(experiment_name=EXPERIMENT_NAME)
except:
experiment = client.create_experiment(EXPERIMENT_NAME)

print(experiment)
```

以下代码片段将为我们已转储到该位置的 zip 创建一次运行：

```
arguments = {}
run_name = pipeline_func.__name__ + 'heart_run'
run_result = client.run_pipeline(experiment.id, run_name, pipeline_filename,arguments)
print(experiment.id)
print(run_name)
print(pipeline_filename)
print(arguments)
```

流水线准备就绪后，点击运行链接。以下是我们的流水线训练情况：

![](img/8f8a671916d96b455297952d0f37b96c_223_0.png)

图 3.11：Kubeflow 端到端流水线

下图是我们创建的流水线，以及 Python 可视化、ROC 曲线、混淆矩阵和 Tensorboard：

![](img/8f8a671916d96b455297952d0f37b96c_224_0.png)

图 3.12：流水线可视化

从 UI 运行流水线的另一种方式如下：

点击创建新实验按钮后，它将重定向到实验创建页面的新屏幕。

![](img/8f8a671916d96b455297952d0f37b96c_225_0.png)

图 3.13：创建实验

提供一个实验名称。

![](img/8f8a671916d96b455297952d0f37b96c_225_1.png)

图 3.14：创建实验并提供名称

点击跳过此项

![](img/8f8a671916d96b455297952d0f37b96c_225_2.png)

参数将在您选择流水线后出现

开始  跳过此步骤  必须选择流水线版本

图 3.15：创建实验跳过步骤

现在，实验已准备就绪；现在点击

![](img/8f8a671916d96b455297952d0f37b96c_226_0.png)

图 3.16：创建运行

接下来，上传我们在之前构建流水线期间创建的 zip 文件。

![](img/8f8a671916d96b455297952d0f37b96c_227_0.png)

图 3.17：上传流水线 tar 或 yaml 文件

现在，创建您已上传的该流水线的运行，并选择我们之前创建的实验。

![](img/8f8a671916d96b455297952d0f37b96c_228_0.png)

图 3.18：选择实验开始运行

接下来，让我们看看如何自动扩缩 KF-Serving 端点并在 Grafana 仪表板中监控它。

## 3.7. 服务端点的自动扩缩容

Knative 的主要功能之一是对应用程序的副本进行自动扩缩，以紧密匹配传入需求，包括在没有流量接收时将应用程序缩减为零。Knative Serving 默认使用 **Knative Pod Autoscaler** 启用此功能。Autoscaler 组件监视流向应用程序的流量，并根据配置的指标对副本进行向上或向下扩缩。

部署 kf-serving Knative 服务：

### Custom_auto_scale.yaml:

```yaml
apiVersion: serving.kubeflow.org/v1alpha2
kind: InferenceService
metadata:
annotations:
sidecar.istio.io/inject: "false"
autoscaling.knative.dev/target: "10"
labels:
controller-tools.k8s.io: "1.0"
name:
namespace: kubeflow
spec:
default:
predictor:
```

```
minReplicas: 1
custom:
container:
image: gcr.io//brain_tumor_scan/kf_serving_braintest:v1
imagePullPolicy: Always
```

```
name: user-container
imagePullSecrets:
- name: user-gcp-sa
```

使用以下命令连接到 GCP 集群：

```
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
```

通过在集群中部署它来创建推理服务：

```
kubectl apply -f custom_autoscale.yaml
```

检查推理服务。间隔一段时间后尝试检查是否已创建：

```
kubectl get inferenceservice -n kubeflow
```

![](img/8f8a671916d96b455297952d0f37b96c_230_0.png)

图 3.19：KF – Serving 自动扩缩推理服务就绪

我们可以使用任何负载测试工具来模拟负载。在这里，我们将使用 Hey 工具来测试自动扩缩：

```bash
# on macOS
brew install hey
```

我们已在第 1 章《Kubeflow 和 Kubernetes 云简介》部分安装了 Prometheus，如果您尚未安装，请参阅该章节。

发送 30 秒的流量，保持 50 个并发请求：

```bash
MODEL_NAME=kfserving-braintumor
HOST=$(kubectl get inferenceservice -n kubeflow $MODEL_NAME -o jsonpath='{.status.url}' | cut -d \"\/\" -f 3)
INPUT_PATH=@./data.json
CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
hey -z 30s -c 100 -m POST -H \"Host: ${HOST}\" -d $INPUT_PATH
```

摘要：
  总计：30.9381 secs
  最慢：2.4160 secs
  最快：0.3205 secs
  平均：0.6304 secs
  请求/秒：155.6978

响应时间直方图：
  0.321 [1]
  0.530 [928]
  0.740 [3435]
  0.949 [326]
  1.159 [45]
  1.368 [25]
  1.578 [0]
  1.787 [30]
  1.997 [21]
  2.206 [4]
  2.416 [2]

延迟分布：
  10% in 0.4698 secs
  25% in 0.5516 secs
  50% in 0.6244 secs
  75% in 0.6655 secs
  90% in 0.7328 secs
  95% in 0.8477 secs
  99% in 1.6786 secs

详情（平均、最快、最慢）：
  DNS+dialup: 0.0184 secs, 0.3205 secs, 2.4160 secs
  DNS-lookup: 0.0000 secs, 0.0000 secs, 0.0000 secs
  req write: 0.0000 secs, 0.0000 secs, 0.0004 secs
  resp wait: 0.3716 secs, 0.3189 secs, 2.2550 secs
  resp read: 0.0000 secs, 0.0000 secs, 0.0012 secs

状态码分布：
  [404] 4817 responses

图 3.20：Hey 流量报告

查看正在运行的 Pod。

```bash
kubectl get pods -n kubeflow | grep kfserving-braintumor
```

kfserving-braintumor-predictor-default-xk9np-deployment-582ct7n 1/2 Running 0 53s
kfserving-braintumor-predictor-default-xk9np-deployment-588lp7k 1/2 Running 0 33s
kfserving-braintumor-predictor-default-xk9np-deployment-589mw7n 1/2 Running 0 53s
kfserving-braintumor-predictor-default-xk9np-deployment-58kc4jv 1/2 Running 0 54s
kfserving-braintumor-predictor-default-xk9np-deployment-58qtt6m 1/2 Running 0 31s
kfserving-braintumor-predictor-default-xk9np-deployment-58rq4qz 1/2 Running 0 50s
kfserving-braintumor-predictor-default-xk9np-deployment-58szgg6 1/2 Running 0 27s
kfserving-braintumor-predictor-default-xk9np-deployment-58vk4jm 1/2 Running 0 50s
kfserving-braintumor-predictor-default-xk9np-deployment-58vnbj5 1/2 Running 0 28s
kfserving-braintumor-predictor-default-xk9np-deployment-58wx6cw 1/2 Running 0 31s

图 3.21：自动扩缩的 Pod

打开 Grafana 仪表板。

查看 Knative Serving 扩缩仪表板：

```bash
# use port-forwarding
kubectl port-forward --namespace knative-monitoring $(kubectl get pod --namespace knative-monitoring --selector="app=grafana" --output jsonpath='{.items[0].metadata.name}') 8080:3000
```
