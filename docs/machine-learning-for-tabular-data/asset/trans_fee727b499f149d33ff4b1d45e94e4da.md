

# 第3章 机器学习 vs 深度学习

```python
X_train_list: 训练数据特征。
train.target: 训练数据目标（标签）。
epochs: 训练迭代次数。
batch_size: 每个训练步阶段的样本数。
validation_data: 用于监控性能的验证数据（可选）。
verbose: 训练期间的输出级别（1 显示进度条）。
callbacks: 训练期间执行的回调列表（仅在 early_stop 情况下使用）
```

Gemini 还提供了以下总结：

- 代码根据条件对带有早停机制（early stopping）或不带早停的模型进行训练。
- 早停是一种用于防止过拟合和提高模型泛化能力的技术。
- 早停的具体实现取决于 `callback_list` 的内容。
- 为了为了完全理解其目的，还需要更多关于模型、训练过程和早停标准的上下文信息。

注意 Gemini 在最后一行中如何通过正确指出揭示了其分析的局限性：它指出，仅凭提供的代码片段，它无法推断出关于完整解决方案的所有细节。列表 3.3 列出了在 Keras 模型训练步骤中使用的回调定义代码。这段代码为 Keras 版本的 Airbnb NYC 解决方案增加了额外的复杂度。

列表 3.3 Keras 回调语句

```python
callback_list = []
es = EarlyStopping(monitor=es_monitor, mode=es_mode, verbose=1,
patience = patience_threshold)
callback_list.append(es)
model_path = get_model(path)
os.path.join(model_path, 'modelcheckpoint'+'.str(experiment_number)+'.h5')
c = ModelCheckpoint(save_model_path,
monitor=es_monitor, mode=es_mode,
verbose=1, save_best_only=True)
callback_list.append(mc)
```

- 定义一个早停回调对象，用于指定一旦性能不再提高，训练过程应停止。

- 将第一个回调添加到回调列表中，供训练过程使用。

- 定义一个模型保存回调，以确保在训练运行中具有最佳性能的模型是在训练运行结束时保存的。

- 将第二个回调添加到回调列表中，供训练过程使用。

一旦我们训练好了模型，就希望将其保存到文件中，以便我们可以在另一个会话中加载并执行它，或者作为模型部署的一部分。在简单的示例中，我们在用于训练模型的同一个 notebook 中保存并重新加载模型。为 XGBoost 保存模型：

# 预测纽约 Airbnb 房价

model.save_model(xgb_save_model_path)

对于 Keras，我们不需要显式的语句来保存模型，因为模型会通过模型保存回调自动保存。

以下列表显示了在 XGBoost 中加载模型的代码。

# 列表 3.4 XGBoost 模型加载语句

```python
loaded_saved_model = xgb.XGBClassifier()
loaded_saved_model.load_model(xgb_save_model_path)
```

- 定义一个新的 XGBoost 分类器对象

- 使用你用 `save_model` 语句保存的模型加载新的 XGBoost 分类器对象

用于加载 Keras 模型的语句是：

```python
saved_model = load_model(save_model_path)
```

XGBoost 和 Keras 之间的另一个区别是，如果你尝试加载保存的 XGBoost 分类器模型（如我们为 Airbnb NYC 问题训练的模型）并运行预测，只要你使用的不是当前版本的 XGBoost，就会得到错误。XGBoost 模型训练 notebook 包含以下语句以确保 XGBoost 是最新版本：

```bash
!pip install --upgrade XGBoost
```

在本节中，我们比较了 XGBoost 和 Keras 在数据准备、模型定义、模型训练和模型保存方面的代码简单性。接下来，我们将讨论从这一比较中得出的结论。

# 3.3 结论

从这一比较中我们可以得出以下结论：在数据准备、模型定义、模型训练和模型保存方面，XGBoost 和 Keras 的代码简单性有所异。XGBoost 在数据准备方面更简单，而 Keras 在模型定义方面更直观。在模型训练方面，Keras 提供了更多的灵活性，而在模型保存方面，Keras 更加自动化。

此外，XGBoost 在处理结构化数据时通常比得高效，而 Keras 在处理非结构化数据（如图像、文本）方面更有优势。对于许多表格数据任务，XGBoost 往往优于 Keras。

在数据准备方面，XGBoost 往往更简单；在模型定义方面，Keras 更加直观；在模型训练方面，Keras 提供了更多的灵活性；而在模型保存方面，Keras 更加自动化。

此外，XGBoost 在处理结构化数据时通常比 Keras 更高效，而 Keras 在处理非结构化数据（如图像、文本）方面更有优势。对于许多表格数据任务，XGBoost 往往优于 Keras。

