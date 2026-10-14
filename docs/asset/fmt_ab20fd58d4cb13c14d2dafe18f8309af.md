
```python
####### Define the hyperparameter tuner
tuner = HyperparameterTuner(
    estimator=xgb,
    base_tuning_job_name='bayesian',
    objective_metric_name='validation:accuracy',
    hyperparameter_ranges=hpt_ranges,
    strategy='Bayesian',
    max_jobs=3,  # Reduced from 20 to 3 max jobs
    max_parallel_jobs=3,  # Number of parallel jobs
    objective_type='Maximize'
)
```

#### 6. 启动调优任务

```python
###### Launch the hyperparameter tuning job
tuner.fit({'train': train_data, 'validation': val_data})
tuner.wait()
```

#### 7. 获取最佳模型与结果分析

##### 7.1 获取最佳训练作业名称

```python
####### Get the best training job name
best_training_job_name = tuner.best_training_job()
```

##### 7.2 检索调优结果

```python
####### Retrieve the tuning results
tuning_job_name = tuner.latest_tuning_job.name
tuner_analytics = HyperparameterTuningJobAnalytics(tuning_job_name)
tuner_df = tuner_analytics.dataframe()
```

##### 7.3 提取最佳超参数

```python
####### Extract the best hyperparameters
if 'FinalHyperParameters' in tuner_df.columns:
    best_hyperparameters = tuner_df.loc[tuner_df['TrainingJobName'] == best_training_job_name, 'FinalHyperParameters'].values[0]
else:
    best_hyperparameters = tuner_df.loc[tuner_df['TrainingJobName'] == best_training_job_name].drop(['TrainingJobName', 'FinalObjectiveValue'], axis=1).to_dict('records')[0]
```

##### 7.4 打印最佳结果

```python
####### Print the best training job and hyperparameters
print(f"Best Training Job: {best_training_job_name}")
print("Best Hyperparameters:")
for key, value in best_hyperparameters.items():
    print(f"  {key}: {value}")
```

#### 8. 可视化调优结果

```python
###### Plot the tuning job results
plt.figure(figsize=(12, 8))
plt.scatter(tuner_df.index, tuner_df['FinalObjectiveValue'], label='Tuning Jobs')
plt.scatter(tuner_df.loc[tuner_df['TrainingJobName'] == best_training_job_name].index,
            tuner_df.loc[tuner_df['TrainingJobName'] == best_training_job_name]['FinalObjectiveValue'],
            color='red', marker='*', s=200, label='Best Job')

plt.xlabel('Iteration')
plt.ylabel('Cross-Validation Accuracy')
plt.title('Hyperparameter Tuning Results')

###### Display the best hyperparameters on the plot
best_hyperparameters_str = '\n'.join([f'{key}: {value}' for key, value in best_hyperparameters.items()])
plt.figtext(0.5, -0.15, f'Best Hyperparameters:\n{best_hyperparameters_str}', ha='center', va='top', fontsize=10, bbox=dict(facecolor='lightgrey', alpha=0.5))

###### Update legend position below the x-axis
plt.legend(loc='upper center', bbox_to_anchor=(0.5, -0.2), ncol=3)

###### Save the plot as an image file
output_dir = './ch06/images'
os.makedirs(output_dir, exist_ok=True)
plt.savefig(os.path.join(output_dir, 'tuning_results.png'), bbox_inches='tight')
plt.close()
```

#### 9. 部署 Serverless 端点

##### 9.1 创建 Serverless 推理配置

```python
####### Create a serverless inference configuration
serverless_config = ServerlessInferenceConfig(
    memory_size_in_mb=2048,
    max_concurrency=5
)
```

##### 9.2 定义自定义 Predictor 类

```python
####### Define the custom predictor class (if you have one)
class CustomPredictor(Predictor):
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        # You can add custom initialization code here
```

##### 9.3 检索最佳模型

```python
####### Retrieve the best model from the hyperparameter tuning job
best_model = Model(
    image_uri=xgb_image,
    model_data=f's3://{bucket_name}/{prefix}/output/{best_training_job_name}/output/model.tar.gz',
    role=role,
    sagemaker_session=session,
    predictor_cls=CustomPredictor  # Specify the custom predictor class
)
```

##### 9.4 部署模型

```python
####### Deploy the best model as a serverless endpoint with a unique endpoint name
try:
    predictor = best_model.deploy(
        serverless_inference_config=serverless_config,
        endpoint_name='xgboost-digits-serverless-endpoint-dario',  # Use a unique endpoint name
        serializer=CSVSerializer(),  # Specify CSV serializer
        deserializer=JSONDeserializer()  # Optional: Specify a deserializer
    )
    print(f"Successfully deployed serverless endpoint: {predictor.endpoint_name}")
except Exception as e:
    print("Failed to deploy serverless endpoint")
    print(e)
    predictor = None
```

#### 10. 推理测试

```python
###### Example inference
if predictor is not None:
    test_sample = X_test[0].reshape(1, -1)
    test_sample_csv = ','.join(map(str, test_sample.flatten()))  # Convert numpy array to CSV-encoded string
    result = predictor.predict(test_sample_csv)
    print('Prediction for the first test sample:', result)
else:
    print("Cannot perform inference because the predictor object is None")
```

#### 11. 保存测试样本图像

```python
###### Plot and save the test sample image without extra data points
plt.figure(figsize=(4, 4))
image_sample = X_test[0].reshape(8, 8)
output_image_path = os.path.join(output_dir, 'test_sample_image.png')
plt.imshow(image_sample, cmap='gray')
plt.title(f"Test sample label (actual digit): {y_test[0]}")
plt.axis('off')  # Turn off the axis
plt.savefig(output_image_path)
plt.close()

print(f"Test sample image saved to: {output_image_path}")
```

因为我们已经在第 5 章介绍了该程序的模型调优方面，现在让我们专注于该程序如何部署最佳模型。

部署阶段涉及几个关键步骤，以确保模型能够高效地处理推理请求。首先，程序设置一个无服务器推理配置对象 `ServerlessInferenceConfig`，指定内存大小和最大并发数等关键参数，以优化资源分配。此配置可帮助 Amazon SageMaker AI 动态管理为推理请求提供服务所需的计算资源，而无需专用实例。

随后，检索保存在 S3 存储桶中名为 `model.tar.gz` 的最佳训练模型以进行部署。创建 `Model` 对象，指定 `model.tar.gz` 工件文件的 S3 路径和 XGBoost 容器镜像 URI。此容器 (`xgboost:1.2-1`) 旨在与序列化的模型格式无缝配合，确保兼容性和部署的便捷性。

当调用 `Model` 对象的 `deploy` 方法时，Amazon SageMaker 会协调部署过程。容器启动并下载模型工件文件 `model.tar.gz`，并自动解压。解压后的文件被放置在容器内的适当目录中，XGBoost 模型被加载到内存中，准备好为推理请求提供服务。这种自动化确保了模型正确初始化并可用于预测。

为处理推理请求，端点期望输入为 CSV 格式，这通过对输入数据使用 `CSVSerializer` 和对输出数据使用 `JSONDeserializer` 来保证。分配一个唯一的端点名称以避免冲突，并使用 `CustomPredictor` 类来管理与端点的交互。该端点暴露一个 API，用于处理手写数字的 CSV 表示，执行预测并返回结果。

程序通过使用已部署的端点执行示例推理来结束。一个测试样本被转换为 CSV 编码字符串并发送到端点。然后返回并显示预测的数字类别，如图 6.10 所示。

![图 6.10 来自无服务器推理端点的预测。](img/c06f010.png)

图 6.10 来自无服务器推理端点的预测。

正如你所见，模型正确预测了测试样本，该样本是数字 `6` 的 CSV 表示。

图 6.11 显示了无服务器端点。

![图 6.11 无服务器推理端点摘要。](img/c06f011.png)

图 6.11 无服务器推理端点摘要。

请注意图 6.11 底部的端点模型、变体、最大并发数以及我们在代码中以编程方式设置的内存大小。由于其状态为“In service”（服务中），该端点已准备好在指定的 URL 处提供推理请求服务。

Amazon SageMaker Studio 允许你直接从 UI 测试端点。在图 6.12 中，你可以看到通过发送测试样本的 CSV 编码字符串来测试端点的结果。

![图 6.12 测试推理。](img/c06f012.png)

图 6.12 测试推理。

最后，如果你想了解模型的超参数以及为什么它在调优过程中被贝叶斯策略选中，我已在图 6.13 中提供了相关图表。

![图 6.13 模型选择。](img/c06f013.png)

图 6.13 模型选择。

你刚学会了如何以编程方式将模型部署到无服务器推理端点。此部署流程利用 Amazon SageMaker AI 的托管容器和无服务器基础设施的强大功能，确保高效且可扩展地处理推理请求，而无需手动管理资源。

### 摘要

在本章中，你学习了如何让你精心开发和优化的模型准备好工作。如果你的用例适合 AWS AI 服务，AWS 提供了一套完全托管的 AI 服务，可通过 API 调用轻松集成到应用程序中。这些服务包括 Amazon Rekognition、Textract、Polly、Transcribe、Translate、Comprehend、Lex 和 Personalize，它们为各种任务提供预训练模型。因为这些模型托管在托管的 AWS 账户中，用户对底层模型的访问受限；然而，这些预训练模型可以轻松使用，从而实现快速集成和部署，而无需复杂的模型管理。此外，你还了解到 Amazon Bedrock 要求使用代理和 Converse API 的概念以不同方式部署模型，它们充当应用程序和基础模型之间的中介，既提供全面的编排，又提供简化的对话式交互。这一初步步骤为在 AWS 中有效利用 AI 能力奠定了基础。

在使用 AWS AI 服务便捷性的基础上，Amazon SageMaker AI 提供了多种部署选项来管理和托管 ML 模型。这些选项包括用于低延迟预测的实时推理、用于自动扩展的无服务器推理（如深度实践练习所示）、用于处理大负载和长处理时间的异步推理，以及用于批量处理大型数据集的批量推理。每种部署方法旨在满足特定用例，确保模型部署的灵活性和可扩展性。

尽管 Amazon SageMaker AI 提供了强大的托管部署选项，但在某些场景下，非托管模型部署更为合适。这涉及在替代计算平台上部署模型，例如 Amazon EC2 实例、Amazon EKS 集群、AWS Lambda 函数，甚至本地服务器。虽然这种方法需要更多手动工作来进行基础设施设置、扩展和维护，但它提供了对部署环境更大的控制和自定义能力。

为进一步提升模型性能和部署效率，可使用 Amazon SageMaker Neo 针对各种硬件平台优化模型，以降低延迟并提高性能。高级部署技术（如自动扩展和蓝/绿部署——包括一次性、金丝雀和线性策略）支持在模型部署时进行安全且受控的更新。这些方法确保持续改进和稳健的部署策略，使部署过程更具弹性和高效。

最后，你了解到编排 ML 工作流对于管理端到端 ML 生命周期至关重要。Amazon SageMaker Pipelines 提供了一种从数据准备到模型部署自动化工作流的强大方式。此外，Amazon Managed Workflows for Apache Airflow 和 AWS Step Functions 等服务可集成以增强编排能力，从而实现复杂的工作流和条件逻辑。这种编排确保 ML 流程得到简化、可重复且可维护，最终加速模型部署并提高运营效率。

### 考试重点

**了解推理基础设施和训练基础设施的区别。** 推理基础设施通常所需的计算和内存远少于训练基础设施，因为推理仅涉及将预训练模型应用于新数据，而训练涉及从大型数据集中学习和优化模型参数的计算密集型过程。

#### 了解 Amazon SageMaker AI 的托管部署选项

Amazon SageMaker AI 提供四种托管部署选项，以满足不同的用例：

- **实时推理** 为即时预测提供低延迟端点，非常适合交互式应用程序。

- **无服务器推理** 根据流量自动扩展资源，非常适合流量间歇性或不可预测的应用程序。
