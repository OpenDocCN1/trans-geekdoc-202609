
泛化逻辑等。你如何知道哪种超参数组合对你的任务是最好的？

一种方法是简单地尝试许多超参数的组合，并查看哪一个在验证集上表现最好（或使用 K 折交叉验证）。对于这一点，一种方法是直接使用 `GridSearchCV` 或 `RandomizedCV` 来探索超参数空间，就像我们在第 2 章中所做的那样。为了实现这一点，我们需要将模型封装在可能模拟 Scikit-learn 回归器的对象中。创建一个根据一组超参数来构建构建并编译 Keras 模型的函数：

```python
def build_model(n_hidden, n_neurons=30, learning_rate=3e-3, input_shape=[8]):
    model = keras.models.Sequential()
    options = {"input_shape": input_shape}
    for layer in range(n_hidden):
        model.add(keras.layers.Dense(n_neurons, activation="relu", **options))
        options = {}
    optimizer = keras.optimizers.SGD(learning_rate)
    model.compile(loss="mse", optimizer=optimizer)
    return model
```

此函数为单变量回归创建了一个 `Sequential` 模型（只有一个输出神经元），具有给定的输入形状、隐藏层数量和神经元数量，并使用配置了给定学习率的 SGD 优化器对其进行编译。这里 `opts` 字典用于确保第一层被正确赋予了输入形状（如果 `n_hidden=0`，则第一层将是输出层）。像 Scikit-Learn 一样，尽可能为许多超参数提供合理的默认值是一个良好的做法。

接下来，让我们基于这个 `build_model` 函数创建一个 Keras 回归器：

```python
keras_reg = keras.wrappers.KerasRegressor(build_fn=build_model, input_shape=[8])
keras_reg.fit(X_train, y_train, epochs=100, validation_data=(X_valid), callbacks=[EarlyStopping(patience=10)])
mse = keras_reg.score(X_test)
y_pred = keras_reg.predict(X_test)
```

`KerasRegressor` 是对 `build_model` 函数的封装，它模仿了 Scikit-Learn 的接口。由于它遵循 `scikit-learn` 的 API，我们可以像使用普通回归器一样使用它：通过 `fit` 方法训练，通过 `score` 方法评估，通过 `predict` 方法进行预测。为了找到最佳超参数，我们可以使用 `GridSearchCV` 或 `RandomizedCV`：

```python
param_grid = {
    "n_hidden": [1, 2, 3],
    "n_neurons": [30, 50, 100],
    "learning_rate": [1e-2, 1e-3, 1e-4]
}
grid_search = GridSearchCV(keras_reg, param_grid, cv=3)
```_
grid_search.fit(X_train, y_train)
print(grid_search.best_params_)
```

`GridSearchCV` 会尝试所有可能的组合，但如果参数空间很大，这种方法非常耗时。这时使用 `RandomizedCV` 会更有效：

```python
param_dist = {
    "n_hidden": [1, 2, 3],
    "n_neurons": [30, 50, 100],
    "learning_rate": [1e-2, 1e-3, 1e-4]
}
random_search = RandomizedCV(keras_reg, param_dist, n_iter=10, cv=3)
random_search.fit(X_train, y_train)
print(random_search.best_params_)
```

`RandomizedCV` 随机选择 `n_iter` 组组合，通常可以在更短的时间内找到非常优的参数。为了进一步优化，还可以使用贝斯优化（Bayesian Optimization）：

```python
param_dist = {
    "n_hidden": [1, 2, 3],
    "n_neurons": [30, 50, 100],
    "learning_rate": reciprocal(1e-4, 1e-2)
}
bayes_search = BayesianSearchCV(keras_reg, param_dist, n_iter=32, cv=3)
bayes_search.fit(X_train, y_train)
print(bayes_search.best_params_)
```

贝斯优化通过利用之前的结果来选择下一组参数，通常比随机或网格搜索更高效。无论使用哪种方法，超参数调优都是耗时的过程，但对于提升模型性能至关重要。
