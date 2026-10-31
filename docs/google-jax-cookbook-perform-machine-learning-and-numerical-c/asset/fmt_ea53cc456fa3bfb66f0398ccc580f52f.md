
# Checkpointing Long-Running Jobs

If you don't save the model state regularly, unexpected things like power outages, system crashes, or preemptible cloud instances can cause you to lose your training progress. This can be a real waste of time and computing power. The goal is to set up a solid checkpointing plan that saves the model's state at regular intervals during training.

To avoid losing your training progress, you can set up checkpointing to save the model's parameters, optimizer state, and any other info needed to resume training at regular intervals. In `JAX`, you can use built-in utilities that serialize and deserialize the training state efficiently to make checkpointing easier.

## Creating Training State

To begin with, first set up the training state for our defined neural network model, including the model parameters and optimizer.

```python
def create_train_state(rng, learning_rate):
    model = FashionMNISTModel()
    params = model.init(rng, jnp.ones([1, 28, 28]))['params']
    tx = optax.adam(learning_rate)
    return train_state.TrainState.create(apply_fn=model.apply, params=params, tx=tx)
```

Next, define the loss and accuracy metrics:

```python
def compute_metrics(logits, labels):
    loss = optax.softmax_cross_entropy_with_integer_labels(logits, labels).mean()
    accuracy = jnp.mean(jnp.argmax(logits, -1) == labels)
    return {'loss': loss, 'accuracy': accuracy}
```

## Implementing Training Step

Next, we use `jax.jit` to compile the training step for efficiency.

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

## Implementing Checkpointing

Then decide on a directory to store checkpoints and the frequency of saving.

```python
ckpt_dir = './checkpoints'
checkpoint_frequency = 5  # Save a checkpoint every 5 epochs
```

Just tweak the training loop so it saves checkpoints every so often.

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

To quickly summarize the above script, the `checkpoints.save_checkpoint` function saves the entire training state, including model parameters and optimizer state. And, we set the `overwrite=True` to ensure that only the latest checkpoint is kept, so as to save disk space.

## Handling Unexpected Interruptions

In the event of an interruption, you can resume training from the last saved checkpoint.

```python
# Before starting the training loop
state = checkpoints.restore_checkpoint(ckpt_dir, target=state)
# The rest of the training loop remains the same
```

## Customizing Checkpointing Strategies

You can customize the checkpointing strategy based on your needs. You can keep the last N checkpoints and save the model when it achieves the best validation accuracy.

```python
# In the evaluation section
if test_metrics['accuracy'] > best_accuracy:
    best_accuracy = test_metrics['accuracy']
    checkpoints.save_checkpoint(ckpt_dir, target=state, step=state.step, prefix='best_', overwrite=True)
    print('Best model checkpoint saved.')
```

Once done, save the checkpoints asynchronously in order to avoid slowing down the whole training.

## Testing Checkpoint Restoration

Now, before relying on checkpointing for long-running jobs, test that you can save and restore the training state correctly.

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

If you use `Flax`'s utilities to set up checkpoints, you can make sure you don't lose any progress if your training is interrupted. If you save the model's state regularly, you can pick up where you left off with the last checkpoint, which helps you avoid wasting computational effort. This is a must for long-running training jobs, especially when you're using preemptible cloud instances or working in environments where interruptions are common.
