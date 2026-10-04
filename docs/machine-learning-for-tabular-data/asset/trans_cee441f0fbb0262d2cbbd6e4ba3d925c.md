

# 使用生成式 AI 帮助创建 ML流水线

```python
with open(path_to_yaml) as file:
    config = yaml.safe_load(file)
```

第一组由 Gemini for Google Cloud 生成的代码

第二组由 Gemini for Google Cloud 生成的代码

列表 11.10 中的代码与 `get_pipeline_config` 函数的手写代码并不相同，如接下来的的列表所示。

# 列表 11.11 get_pipeline_config 函数：手写版本

```python
def get_pipeline_config(path_to_yaml):
    """读取配置 yaml 文件
    Args:
        path_to_yaml: 包含流水线脚本参数的 yaml 文件
    Returns:
        包含从配置文件读取的参数的字典
    """
    try:
        print('path_to_yaml '+path_to_yaml)
        with open(path_to_yaml, 'r') as c_file:
            config = yaml.safe_load(c_file)
    except Exception as e:
        print('Error reading the config file')
    return config
```

手写代码包含了文件操作的异常处理

手写代码在打开文件时包含了 'r' 参数

将列表 11.10 中 Gemini for Google Cloud 生成的代码与手写代码相比，我们可以看到两个区别：

- 手写代码包含了处理打开配置文件问题时的异常处理。
- 手写代码在文件操作中包含了 'r' 参数。

`get_pipeline_config` 函数非常简单，尽管如此，Gemini for Google Cloud 能够为该函数生成运行代码。

关于 Gemini for Google Cloud 代码生成的的一些考虑因素：

- 你不需要一次性接受 Gemini for Google Cloud 生成的临时代码。要逐个 token 接受临时代码，请按 CTRL + 右方向键来接受单个 token。
- 要拒绝整个临时代码生成并重新开始，请按 ESC 键，整组临时代码将被擦除。

- 当你使用完全相同的输入多次要求 Gemini for Google Cloud 生成代码时，无法保证获得完全相同的代码。例如，在 `get_pipeline_config` 示例中，Gemini for Google Cloud 有时会分步生成该函数，如本节所示，并且

# 第 11 章 构建机器学习流水线

有时它会单步生成整个函数，包括返回（return）语句。

既然我们已经使用 AI 来生成代码，我们将在下一节中查看如何使用它来解释代码。

# 11.4.3 使用 Gemini for Google Cloud 解释 ML流水线的代码

现在我们已经有了 Gemini for Google Cloud 生成代码的示例，让我们练习它的解释代码的能力。

要让 Gemini for Google Cloud 解释代码段，请将以下代码（脚本中的主函数）放入 Cloud Shell Editor 中的新文件中。

```python
# 列表 11.12 获取流水线配置函数
if __name__ == '__main__':
    start_time = time()
    # 加载流水线配置参数
    config = get_pipeline_config('pipeline_config.yml')
    # 发送到训练的所有参数
    # 在容器中运行的脚本通过
    # Cloud Storage 中的一个 yaml 文件发送，其 URI 是唯一的参数
    model_args = ['--config_bucket', config['bucket_path']]
    print(f'model_args: {model_args}')
    # 创建 CustomTrainingJob 对象
    job = create_job(config)
    # 定义用于运行 CustomTrainingJob 的 Dataset 对象
    dataset_path = f'/projects/{config['project_id']}/\n/locations/{config['region']}/\n/datasets/{config['dataset_id']}'
    ds = aiplatform.Dataset(dataset_path)
    # 运行 CustomTrainingJob 对象以获取训练后的模型
    model = run_job(job, ds, model_args)
    print("deployment starting")
    # 部署到 Vertex AI 端点
    if config['deploy_model']:
        deploy_model(model, config)
    print("deployment completed")
    # 显示脚本运行时间
    print(f"--- {time.time() - start_time} seconds ---")
```

一旦你将 11.13 中的代码粘贴到文件中，选择它，然后从 Cloud Shell Editor 工具栏上选择 Gemini for Google Cloud Smart Actions 图标（见图 11.41）。

![](img/def89cc476fa39f4c54bd34e78d91674_454_0.png)

在出现的菜单中，选择 Explain（解释），如图 11.42 所示。

```
自定义（例如，简化我的代码）
- 生成代码
- 解释此
- 生成单元测试
```

图 11.42 Gemini for Google Cloud Smart Actions 图标

当你选择此项时，代码的解释将出现在 Cloud Shell Editor 的左侧窗格中，如图 11.43 所示。

（注：原文后续存在大量重复段落，根据指令“不要重复输出原文”的原则，此处仅保留核心逻辑翻译说明）

