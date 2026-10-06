
## GAN 目标函数

```elixir
defn g_objective(
  d_params,
  g_params,
  discriminator_fn,
  generator_fn,
  real_batch
) do
  batch_size = Nx.axis_size(real_batch, 0)
  real_targets = Nx.broadcast(1, {batch_size, 1})
  latent = Nx.random_normal({batch_size, 128})

  %{prediction: fake_batch} = generator_fn.(g_params, latent)
  %{prediction: fake_labels} = discriminator_fn.(d_params, fake_batch)

  Axon.Losses.binary_cross_entropy(
    real_targets,
    fake_labels,
    reduction: :mean
  )
end
```

此实现类似于判别器的目标函数。你使用生成器生成一个假批次，然后使用判别器为该批次生成一组标签。但你应该注意损失计算中的细微差别。目标不是尝试给假图像分配假标签，而是欺骗判别器给假图像分配真标签。生成器通过学习欺骗判别器，隐式地学会生成与训练数据相似的数据。

## 初始化状态

现在你需要为训练循环实现一个初始化函数。根据你的训练步骤，状态需要包含 `:model_state`、`:optimizer_state` 和 `:loss`，分别用于 `"generator"` 和 `"discriminator"`，以及一个用于跟踪当前迭代的计数器：

```elixir
defn init_state(
  discriminator_init_fn,
  generator_init_fn,
  discriminator_optimizer_init,
  generator_optimizer_init,
  batch,
  init_state
) do
  d_params = discriminator_init_fn.(batch, init_state)
  g_params = generator_init_fn.(Nx.random_normal({64, 128}), init_state)
  d_optimizer_state = discriminator_optimizer_init.(d_params)
  g_optimizer_state = generator_optimizer_init.(g_params)

  model_state = %{
    "discriminator" => d_params,
    "generator" => g_params
  }
  optimizer_state = %{
    "discriminator" => d_optimizer_state,
    "generator" => g_optimizer_state
  }
  loss = %{
    "discriminator" => Nx.tensor(0.0),
    "generator" => Nx.tensor(0.0)
  }

  %{
    model_state: model_state,
    optimizer_state: optimizer_state,
    loss: loss,
    i: Nx.tensor(0)
  }
end
```

这里没有新内容。你初始化两个模型及其各自的优化器，然后为要跟踪的每个项目构建映射。

## 显示样本

与 VAE 一样，你可能还想跟踪生成器在各轮次之间生成图像的效果。你可以通过将上一节的 `display_sample/2` 函数转换为此示例来实现：

```elixir
def display_sample(
  %Axon.Loop.State{step_state: state} = out_state,
  generator_fn
) do
  latent = Nx.random_normal({3, 128})
  %{prediction: out} = generator_fn.(state[:model_state]["decoder"], latent)
  out_image = Nx.multiply(out, 255) |> Nx.as_type(:u8)
  upsample = Axon.Layers.resize(
    out_image,
    size: {512, 512},
    channels: :first
  )
  for i <- 0..2 do
    Kino.Image.new(Nx.reshape(upsample[i], {512, 512, 1})) |> Kino.render()
  end
  {:continue, out_state}
end
```

## 自定义训练循环

最后一步是实现自定义训练循环。总体而言，该过程类似于 VAE 示例。首先使用以下代码构建两个模型的初始化和预测函数：

```elixir
{discriminator_init_fn, discriminator_fn} =
  Axon.build(discriminator, mode: :train)

{generator_init_fn, generator_fn} =
  Axon.build(generator, mode: :train)
```

接下来，你需要为每个模型构建优化器：

```elixir
{d_optimizer_init, d_optimizer} = Axon.Optimizers.adam(1.0e-4)
{g_optimizer_init, g_optimizer} = Axon.Optimizers.adam(1.0e-3)
```

请注意，你为每个模型使用了略微不同的优化器。为了防止判别器在生成器训练初期占据主导地位，你需要降低判别器的学习率。GAN 训练非常敏感——请随意尝试不同的超参数和优化器，看看能否找到更好的配置。

现在你可以实现初始化和步进函数的参数化形式：

```elixir
init_fn = &GAN.init_state(
  discriminator_init_fn,
  generator_init_fn,
  d_optimizer_init,
  g_optimizer_init,
  &1,
  &2
)

step_fn = &GAN.train_step(
  discriminator_fn,
  generator_fn,
  d_optimizer,
  g_optimizer,
  &1,
  &2
)
```

最后，你可以运行训练循环：

```elixir
step_fn
|> Axon.Loop.loop(init_fn)
|> Axon.Loop.handle(
  :epoch_completed,
  &GAN.display_sample(&1, generator_fn)
)
|> Axon.Loop.log(fn
  %Axon.Loop.State{epoch: epoch, iteration: iter, step_state: state} ->
    d_loss = state[:loss]["discriminator"]
    g_loss = state[:loss]["generator"]
    "\rEpoch: #{epoch}, batch: #{iter},"
    <> " d_loss: #{Nx.to_number(d_loss)},"
    <> " g_loss: #{Nx.to_number(g_loss)}"
end, event: :iteration_completed, device: :stdio)
|> Axon.Loop.run(train_data, %{}, compiler: EXLA, epochs: 10)
```

训练期间，你将看到类似以下输出：

```
Epoch: 2, batch: 827, d_loss: 0.722309589, g_loss: 0.9743837
```
