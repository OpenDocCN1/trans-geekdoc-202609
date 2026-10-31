
# 长时间运行任务的检查点

如果你不定期保存模型状态，像停电、系统崩溃或可抢占云实例之类的意外情况可能会导致你丢失训练进度。这会造成时间和计算资源的真正浪费。目标是建立一个稳健的检查点计划，在训练期间以固定间隔保存模型的状态。

为了避免丢失训练进度，你可以设置检查点以定期保存模型的参数、优化器状态以及恢复训练所需的任何其他信息。在 `JAX` 中，你可以使用内置工具高效地序列化和反序列化训练状态，从而使检查点操作更简单。

## 创建训练状态

首先，设置我们定义的神经网络模型的训练状态，包括模型参数和优化器。

```python
def create_train_state(rng, learning_rate):
    model = FashionMNISTModel()
    params = model.init(rng, jnp.ones([1, 28, 28]))['params']
    tx = optax.adam(learning_rate)
    return train_state.TrainState.create(apply_fn=model.apply, params=params, tx=tx)
```

接下来，定义损失和准确率指标：

```python
def compute_metrics(logits, labels):
    loss = optax.softmax_cross_entropy_with_integer_labels(logits, labels).mean()
    accuracy = jnp.mean(jnp.argmax(logits, -1) == labels)
    return {'loss': loss, 'accuracy': accuracy}
```

## 实现训练步骤

接下来，我们使用 `jax.jit` 编译训练步骤以提高效率。

```python
@jit
def train_step(state, batch):
    def loss_fn(params):
        logits = FashionMNISTModel().apply({'params': params}, batch['images'])
        loss = optax.softmax_cross_entropy_with_integer_labels(logits, batch['labels']).mean()
        return loss
    grads = grad(loss_fn)(state.params)
    state = state.apply_gradients(grads=grads)
    return state
```

## 实现检查点

然后确定用于存储检查点的目录和保存频率。

```python
ckpt_dir = './checkpoints'
checkpoint_frequency = 5  # Save a checkpoint every 5 epochs
```

只需调整训练循环，使其定期保存检查点。

```python
import os
num_epochs = 50  # Example for a long-running job
rng = random.PRNGKey(0)
state = create_train_state(rng, learning_rate=0.001)
# Restore from the latest checkpoint if available
state = checkpoints.restore_checkpoint(ckpt_dir, target=state)
# Determine the starting epoch
start_epoch = int(state.step / len(train_ds))
for epoch in range(start_epoch, num_epochs):
    for batch in train_ds:
        state = train_step(state, batch)
    # Update the training step (epoch)
    state = state.replace(step=state.step + len(train_ds))
    # Save a checkpoint every 'checkpoint_frequency' epochs
    if (epoch + 1) % checkpoint_frequency == 0:
        checkpoints.save_checkpoint(ckpt_dir, target=state, step=state.step, overwrite=True)
        print(f'Checkpoint saved at step {state.step}')
    # Optionally, evaluate on the test set
    # ... (evaluation code)
    print(f'Epoch {epoch + 1} completed.')
```

为了快速总结上述脚本，`checkpoints.save_checkpoint` 函数会保存整个训练状态，包括模型参数和优化器状态。而且，我们设置 `overwrite=True` 以确保只保留最新的检查点，从而节省磁盘空间。

## 处理意外中断

在发生中断的情况下，你可以从最近保存的检查点恢复训练。

```python
# Before starting the training loop
state = checkpoints.restore_checkpoint(ckpt_dir, target=state)
# The rest of the training loop remains the same
```

## 自定义检查点策略

你可以根据需要自定义检查点策略。你可以保留最近的 N 个检查点，并在模型达到最佳验证准确率时保存模型。

```python
# In the evaluation section
if test_metrics['accuracy'] > best_accuracy:
    best_accuracy = test_metrics['accuracy']
    checkpoints.save_checkpoint(ckpt_dir, target=state, step=state.step, prefix='best_', overwrite=True)
    print('Best model checkpoint saved.')
```

完成后，以异步方式保存检查点，以免减慢整个训练速度。

## 测试检查点恢复

现在，在依赖检查点进行长时间运行任务之前，请测试你是否能正确保存和恢复训练状态。

```python
# Simulate interruption
checkpoints.save_checkpoint(ckpt_dir, target=state, step=state.step, overwrite=True)
print('Simulating interruption...')
# Reset state
state = create_train_state(rng, learning_rate=0.001)
# Restore state
state = checkpoints.restore_checkpoint(ckpt_dir, target=state)
print('State restored. Resuming training...')
```

如果你使用 `Flax` 的工具来设置检查点，就可以在训练中断时确保不会丢失任何进度。如果定期保存模型状态，你可以使用最近的检查点继续上次中断的地方，这有助于避免浪费计算资源。对于长时间运行的训练任务来说这是必不可少的，尤其是在使用可抢占云实例或在中断较为常见的环境中工作时。
