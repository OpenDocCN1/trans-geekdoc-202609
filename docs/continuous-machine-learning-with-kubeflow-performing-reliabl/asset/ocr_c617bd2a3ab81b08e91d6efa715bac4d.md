# Save Files:

Anything which was saved in the **wandb.run.dir** directory, will be uploaded to Weight & Biases and saved along with our run when it completes training, which is convenient for saving the literal Weights & Biases for our trained model. By default, this will save to a new subfolder for the files associated with your run, created in **wandb.run.dir** (which is **./wandb** by default).

```
wandb.save("mymodel.h5")
```

We can pass the full path to the Keras or Tensorflow model API.

```
model.save(os.path.join(wandb.run.dir, "mymodel.h5"))
```

Awesome! Next, run your script normally and it will sync the logs in a backend process. This will be your terminal output, metrics, logs and files, and will be synced to the cloud, alongside the record of our git state if we are running from a git repo.

![](bbox=[0.12, 0.71, 0.88, 0.93])