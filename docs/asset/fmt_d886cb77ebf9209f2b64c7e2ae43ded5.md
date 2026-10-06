
这表明你的模型在测试数据中正确预测了约 99% 的数字。这已经很不错了。当然，模型的目的是在新数据上进行预测，那么如何使用 `Axon` 来实现呢？

## 使用 `Axon` 执行模型

`Axon` 提供了编译和运行 `Axon` 模型的执行 API。首先，从 `test_data` 中获取一个单独的图像批次：

```elixir
{test_batch, _} = Enum.at(test_data, 0)
```

为了简化，取出单张图像：

```elixir
test_image = test_batch[0]
```

你可以使用 `Nx.to_heatmap` 来可视化图像：

```elixir
test_image
|> Nx.reshape({28, 28})
|> Nx.to_heatmap()
```

你会看到类似于 图像 的内容。

![images/GettingDeepWithAxon/TestImage.png](img/TestImage.png)

在这个示例中，测试图像是 3，模型应该将 3 作为最可能的标签预测。

现在，你拥有所有需要的东西来对模型进行预测：一个模型、一个与模型兼容的模型状态以及一个输入。最简单的查询方式是先使用 `Axon.build/2` 构建模型，然后调用返回的 `predict_fn`。`Axon.build/2` 将模型转换为一个包含 `{init_fn, predict_fn}` 的元组。`init_fn` 是一个二元函数，用于初始化模型的参数。`predict_fn` 是一个二元函数，接受模型参数和输入张量或张量集合，并返回运行完整模型的结果。

运行以下代码尝试查询模型的预测：

```elixir
{_, predict_fn} = Axon.build(model, compiler: EXLA)
predict_fn.(trained_model_state, test_image)
```

你会看到以下错误信息：

```text
** (Axon.CompileError) exception found when compiling layer
Axon.Layers.dense/4 named dense_0:

** (ArgumentError) Axon.Layers.dense: expected input shape to have at
least rank 2, got rank 1
(axon 0.5.1) lib/axon/shared.ex:92: Axon.Shared.assert_min_rank!/4
(nx 0.5.1) lib/nx/defn/compiler.ex:203: Nx.Defn.Compiler.__remote__/4
(axon 0.5.1) lib/axon/layers.ex:125: Axon.Layers."__defn:dense_impl__"/4
```

发生了什么？请记住 `Axon` 要求输入形状相对静态并符合模型创建时指定的形式。在此例中，你的 `test_image` 缺少一个额外的维度，可以使用 `Nx.new_axis` 在维度 0 上添加一个维度：

```elixir
probabilities =
  test_image
  |> Nx.new_axis(0)
  |> then(&predict_fn.(trained_model_state, &1))
```

你会看到类似的输出：

```text
#Nx.Tensor<
  f32[1][10]
  EXLA.Backend<host:0, 0.4078460682.4224843782.56655>
  [
    [6.16645411355421e-5, 0.011110336519777775, 0.07432620227336884, ...]
  ]
>
```

请记住，你的模型会输出十个与标签 0 到 9 对应的概率。你可以通过计算 `Nx.argmax` 来获取离散标签：

```elixir
probabilities |> Nx.argmax()
```

这将给出以下输出：

```text
#Nx.Tensor<
  s64
  EXLA.Backend<host:0, 0.4078460682.4224843782.56658>
  3
>
```
