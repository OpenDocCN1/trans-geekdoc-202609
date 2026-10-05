
# 第 5 章 超参数优化服务

## HPO 服务设计原则

HPO 服务需要忽略训练代码和模型训练框架。除了支持 TensorFlow、PyTorch 和 MPI 等任意机器学习框架外，我们希望能够调优用任何编程语言编写的训练代码超参数。

### 原则 2：支持不同 HPO 算法的扩展性与一致性

从 5.2.2 节关于 HPO 算法的讨论中，我们知道超参数搜索算法是 HPO 过程的大脑。超参数搜索的效率决定了 HPO 的性能。良好的 HPO 算法可以在较大的超参数搜索空间和少量试验次数内找到最优超参数。

由于 HPO 研究是一个活跃的领域，每个月都会发布新算法。我们的 HPO 服务需要轻松集成这些新算法，并将作为算法选项提供给客户（数据科学家）。新的算法在用户体验上应与现有算法保持一致。

### 原则 3：可扩展性与容错性

除了 HPO 算法，HPO 服务的另一个责任是管理资源。从实验的角度来看，我们希望在集群和试验层面支持自动伸缩。系统需要根据负载调整集群大小。容错性也很重要；如果试验失败，系统应该能够恢复。HPO 服务需要跟踪每次试验的状态，以便在失败时从检查点恢复。

### 原则 4：多租户

HPO 服务必须为不同的用户或组提供隔离。这将确保不同用户的活动保持在自己的边界内。

### 原则 5：可移植性

如今，"云中立"的概念变得非常流行。人们希望在亚马逊云服务（AWS）、谷歌云平台（GCP）和 Azure 上运行 HPO，因此 HPO 服务需要与底层基础设施解耦。

## 5.3.2 通用 HPO 服务

HPO 系统设计（图 5.9）是标准的，适用于许多场景。它由三个主要组件组成：API 接口、HPO 管理器和超参数（HP）建议器。

接口 A 是 HPO 任务的入口。为了启动 HPO 实验，用户向接口提交 HPO 请求（步骤 1）；请求提供了模型代码（例如 Docker 镜像）、超参数及其搜索空间以及 HPO 算法。

HPO 管理器 B 是 HPO 服务的核心组件；它管理客户请求的 HPO 实验。对于每个请求，作业管理器启动 HPO 试验循环（步骤 2）。在循环内部，它首先调用建议器获取一组建议超参数值（步骤 2.a），然后创建一个试验使用这些超参数值运行模型（步骤 2.b 和 2.c）。

建议器 C 是针对不同 HPO 算法的封装/适配器。它为用户提供了一个统一的接口来选择算法，而无需担心执行细节。要添加新的 HPO 算法，必须在该建议器组件中注册，以成为用户的算法选项。

## HPO 服务端到端执行工作流

让我们看看图 5.9 所示的端到端用户工作流。为了方便，我们重复了图 5.9，此处展示为图 5.10。

![](img/9dbecddeac1b6cad2e240ace2b0d4b22_171_0.png)

图 5.10 HPO 服务的通用系统

首先，用户向 API 接口启动 HPO 请求（步骤 1）。请求定义了训练代码、超参数列表及其值搜索空间、训练目标以及 HPO 算法。然后，HPO 管理器为该请求启动 HPO 试验循环（步骤 2）。该循环启动一系列试验以确定哪组超参数值效果最好。最后，当试验预算...运行耗尽或某次试验达到训练目标，试验循环将中断，并返回最佳超参数（步骤 3）。

在试验循环内部，任务管理器首先查询超参数（HP）建议生成器以推荐超参数候选方案（步骤 2.a）。建议生成器将运行选定的 HP 算法来计算一组超参数值并将其返回给任务管理器（步骤 2.b）。任务管理器创建一个试验，使用建议的超参数值启动模型训练过程（步骤 2.c）。该试验还会监控训练过程，并持续向试验数据库报告指标，直到训练完成（步骤 2.d）。当任务管理器完成当前试验时，它会完成试验历史（过去试验中的试验指标和使用的超参数值），并将其传递给 HP 建议生成器以获取新的超参数候选集（步骤 2.e）。

由于 HPO 的用例是标准且通用的，并且已经有多个开箱即用的开源 HPO 项目，我们认为学习如何使用它们比重建一个没有额外价值的新系统更好。在附录 C 中，我们将向你介绍一种强大且高度可移植的基于 Kubernetes 的 HPO 服务——Keflow Katib。

## 5.4 开源 HPO 库

对于小型数据科学家团队来说，HPO 服务可能显得开销太大，特别是当他们所有的模型都在他们自己管理的几台服务器上进行训练时。在这种情况下，使用 HPO 库在本地机器或托管集群（小规模，1-10 台服务器）上优化模型训练是更好的选择。

在本节中，我们将介绍三个实用的 HPO 开源库：Optuna、Hyperopt 和 Ray Tune。它们都作为 HPO 库运行，易于学习且使用简单。由于 Optuna、Hyperopt 和 Ray Tune 都能找到找到入门文档和合适的示例，我们将重点介绍通用概述和功能介绍，以便你根据自己的情况决定使用哪一个。

在后续关于不同 HPO 库的讨论中，特别是在"如何使用"部分，你会频繁看到"目标函数"（objective function）一词。什么是目标函数？图 5.11 展示了这一过程。

### 目标函数

![](img/9dbecddeac1b6cad2e240ace2b0d4b22_172_0.png)

图 5.11 目标函数接收超参数作为输入并返回分数。

对于 HPO 算法（如贝叶斯搜索），为了生成让下次试验效果更好的超参数建议，它需要知道之前的 HPO 试验是如何运行的。因此，HPO 算法要求我们定义一个函数对每次试验评分，并在后续试验中继续最小化或最大化函数的返回值（分数）。我们将其称为目标函数。

在图 5.11 中，我们看到目标函数接收超参数作为输入并返回一个值或分数。目标函数使用给定的超参数执行模型训练，并在训练完成后评估输出模型。

### 5.4.1 Hyperopt

Hyperopt (http://hyperopt.github.io/hyperopt/#getting-started) 是一个轻量级且易用的用于串行和并行 HPO 的 Python 库。随机搜索、TPE 和自适应 TPE 是 Hyperopt 中实现的三个 HPO 算法。贝叶斯优化算法（基于高斯过程）和回归树在本书编写时已设计用于接纳，但尚未实现。

#### 如何使用

假设你想知道哪种分类器最适合你的深度学习案例。我们可以通过三个步骤使用 Hyperopt 来获取答案。

首先，我们定义一个目标函数，该函数基本上是实际训练代码的封装函数，但它从 `args` 变量中读取超参数值。其次，我们为选定的超参数定义搜索空间。第三，我们选择一种 HPO 算法，它从搜索空间中选择超参数值并将其传递给目标函数以开始优化过程。列表 5.1 实现了这一场景。

在这个示例中，我们想要确定哪种分类器能带来最佳模型准确率，因此我们在三个候选者：`naive_bayes`、`svm` 和 `dtree` 之间优化 `classifier_type` 超参数。你可能还会注意到，每个分类器都有自己的值搜索空间，例如在 `svm fmin`（步骤 3）中对应 `hp.lognormal('svm_rbf', 0, 1)`；我们在目标函数和搜索空间中将 `TYPE` 指定为具有 10 次最大试验的 HPO 算法。

列表 5.1 开始使用 Hyperopt

```python
# 步骤 1：定义目标函数
def objective(args):
    model = train(args) # 使用传入的超参数训练模型
    return evaluate(model) # 评估结果并返回结果

# 步骤 2：为超参数定义搜索空间
space = hp.choice('classifier_type', [ # 声明三个
    {'type': 'naive_bayes'},
    {'type': 'svm',
        'C': hp.lognormal('svm_C', 0, 1),
        'kernel': hp.choice('svm_kernel', [
            'type': 'linear',
            'type': 'RBF',
            'width': hp.lognormal('svm_rbf_width', 0, 1)]
        ]), # 为 SVM 分类器的
                          参数定义
                          搜索空间
    {'type': 'dtree',
        'criterion': hp.choice('dtree_criterion',
            ['gini', 'entropy']),
        'max_depth': hp.choice('dtree_max_depth',
            [None, hp.lognormal('dtree_depth_int', 3, 1)]),
        'min_samples_split': hp.lognormal(
            'dtree_min_samples_split', 2, 1,)
    }
)
```

```python
# 步骤 3：开始执行 hpo 过程
best = fmin(objective, space, algo=tpe.suggest,
    max_evals=100)
```

`fmin` 函数使用选定的算法在空间上最小化目标函数。

#### 并行化

Hyperopt 是一个独立的库，我们可以在机器集群上并行运行它，并让它们与中央数据库通信协调。Hyperopt 还可以使用 Spark 在不同机器上运行 Hyperopt 工作节点。你可以查看以下文章获取更多细节："On Using Hyperopt: Advanced Machine Learning" (http://mng.bz/PxswR) 和 "Scaling Out Search with Apache Spark" (http://hyperopt.github.io/scaleout/spark/)。

#### 何时使用

Hyperopt 是小型或早期阶段模型训练项目的良好选择。首先，它易于使用。你可以在本地机器或直接访问的服务器上通过三个步骤运行 HPO。其次，它便于修改。因为它采用库的方法，HPO 代码与训练代码放在同一个项目中。通过尝试不同的优化计划（如调整不同的超参数），它非常方便。

### 5.4.2 Optuna

与 Hyperopt ，Optuna 也是一个用于自动化超参数搜索的轻量级 Python 库。它支持大空间搜索和对不利试验的早期剪枝，以及多线程或进程并行。

在我们看来，Optuna 是 Hyperopt 的高级版本，它的可视化功能强大得多。通过图表查看参数之间的相互作用，超参数搜索的可视化提供了大量见解，让你轻松判断哪些参数比其他参数更有效。Optuna 的可视化非常漂亮且具有交互性。

Optuna 相比 Hyperopt 的另一个优势是它的文档。Optuna 的文档非常优秀。除了详细的 API 文档和组织良好的教程外，它维护了一个非常活跃且不断增长的社区，未来会有更多的功能和 GitHub 拉 请求。

#### 如何使用

列表 5.2 展示了使用 Optuna 的快速三步示例：步骤 1，定义目标函数；步骤 2，创建一个代表 HPO 过程的试验对象；步骤 3，使用最大试验配额启动 HPO 过程。

与 Hyperopt 相比，Optuna 要求在目标函数（objective function）中定义更多的 HPO 逻辑。通用代码模式如下：首先，定义搜索空间并通过 `trial.suggest_xxx` 函数生成每次实验的超参数值。接下来，使用采样的超参数值开始训练。然后运行评估方法计算模型性能并返回目标值。在接下来的示例中，评估分是通过 `mean_squared_error` 计算的。你可以在 https://github.com/optuna/optuna-examples 找到更多 Optuna 示例。

列表 5.2 Optuna 入门

```python
# Step 1: 定义一个目标函数
def objective(trial):
    regressor_name = trial.suggest_categorical(
        'classifier', ['SVR', 'RandomForest'])
    if regressor_name == 'SVR':
        svr_c = trial.suggest_float(
            'c', 1e-3, 1e3, log=True)
        regressor_obj = sklearn.svm.SVR(c=svr_c)
    else:
        rf_max_depth = trial.suggest_int('rf_max_depth', 2, 32)
        regressor_obj = sklearn.ensemble.
            RandomForestRegressor(rf_max_depth=rf_max_depth)

X_train, X_val, y_train, y_val = sklearn.model_selection.train_test_split(X, y, random_state=0)

regressor_obj.fit(X_train, y_train)
y_pred = regressor_obj.predict(X_val)

error = sklearn.metrics.
    mean_squared_error(y_val, y_pred)
return error
```

```python
# Step 2: 通过创建新的 study 开始 HPO。
study = optuna.create_study()

# Step 3: 调用 HPO 过程
study.optimize(objective, n_trials=100)
```

#### 并行化

我们可以使用 Optuna 在单机或机器集群上运行 HPO。分布式执行设置非常简单，可以通过三个步骤完成：首先，启动一个关系型数据库服务器（如 MySQL）；其次，使用参数创建存储（storage）；第三，在多个节点和进程之间共享 study。与 Hyperopt 相比，Optuna 的分布式执行更简单，并且可以从单机扩展到多机，而无需修改代码。

#### 何时使用

Optuna 可以作为 Hyperopt 的替代者；它具有更好的文档、可视化和并行执行能力。对于任何可以在一台或多个机器上运行的深度学习模型训练项目，你可以使用 Optuna 来寻找最优超参数。

对于大型数据科学团队或需要支持多个 HPO 项目的情况，Optuna 会有其限制，因为它需要管理中心集群来提供计算资源。但 Optuna 的并行/分布式执行是手动的；人们需要将代码分发到每个服务器并逐个执行。为了以自动化和编程的方式管理分布式计算作业，可以使用 Kubeflow Katib（附录 C）或 Ray Tune。

### 5.4.3 Ray Tune

Ray Tune (https://docs.ray.io/en/latest/index.html) 为构建分布式应用程序提供了一个简单通用的 API。Ray Tune (https://docs.ray.io/en/latest/tune/index.html) 是一个构建在 Ray 之上的 Python 库，用于大规模 HPO。

Ray Tune 库支持几乎任何机器学习框架，包括 PyTorch、XGBoost 和 Keras。它还支持先进的 HPO 算法，如基于群训练（PBT）、BayesOptSearch 以及 HyperBand/ASHA。此外，Tune 提供了一种集成其他库中 HPO 算法的机制，例如 Hyperopt 集成。

通过使用 Ray 作为分布式执行支持，我们可以用几行代码即可启动多节点 HPO 实验。Ray 将处理代码分发、分布式计算管理和容错。

#### 如何使用

使用 Ray Tune 执行 HPO 任务非常直接。例如，定义一个目标函数。在函数中，使用 `config` 变量返回超参数值，启动模型训练并返回评估分数。其次，定义超参数及其搜索空间。第三，通过将目标函数和搜索空间连接起来启动 HPO 执行。列表 5.3 实现了上述步骤。

列表 5.3 Ray Tune 入门

```python
# Step 1: 定义 objective_function
def objective_function(config):
    model = ConvNet()
    model.to(device)
    optimizer = optim.SGD(
        model.parameters(), lr=config['lr'],
        momentum=config['momentum']
    )
    for i in range(10):
        train(model, optimizer, train_loader)
        acc = test(model, test_loader)
    tune.report(mean_accuracy=acc)

# Step 2: 为每个超参数定义搜索空间
search_space = {
    "lr": tune.sample_from(lambda spec: 10**(-10 * np.random.rand())),
    "momentum": tune.uniform(0.1, 0.9) # 为 "momentum" 在 0.1 到 0.9 之间均匀采样浮点值
}

# 取消此注释以启用分布式执行
# ray.init(address="auto")

# Step 3: 启动 HPO 执行
analysis = tune.run(
    objective_function,
    num_samples=20,
    scheduler=ASHAcheduler(metric="mean_accuracy"),
    config=search_space)

# 查看 HPO 结果
df = analysis.results_dataframe()
```
