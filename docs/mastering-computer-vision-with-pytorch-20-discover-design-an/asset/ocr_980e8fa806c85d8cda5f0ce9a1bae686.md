manage the GPUs and distribute the model. PyTorch Lightning abstracts this complexity, allowing you to train across multiple GPUs or even distributed systems with a few configuration changes.

# Training on Multiple GPUs

To train your model on multiple GPUs, you simply need to specify the number of GPUs in the Trainer configuration. Lightning will automatically distribute the model across the specified GPUs, handle data parallelism, and manage backpropagation.

# Example: Multi-GPU Training

```
trainer = pl.Trainer(max_epochs=10, gpus=2) # Use 2 GPUs for
training
trainer.fit(model, train_dataloader)
```

In this example, specifying gpus=2 allows the Trainer to automatically distribute the model across two GPUs. This eliminates the need for complex manual GPU management.

# Distributed Training

For distributed training across multiple nodes (that is, distributed data parallelism), Lightning simplifies the setup further. By setting the distributed_backend option, you can easily configure distributed training. This is especially useful for large models or datasets that need to be trained on multiple machines.

# Example: Distributed Training

```
trainer = pl.Trainer(max_epochs=10, gpus=2, strategy='ddp') #
Use DDP for distributed training
trainer.fit(model, train_dataloader)
```