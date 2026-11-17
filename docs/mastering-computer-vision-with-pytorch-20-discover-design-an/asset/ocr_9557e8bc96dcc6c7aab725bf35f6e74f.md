Logging metrics such as loss, accuracy, or custom-defined metrics is straightforward in Lightning. You can log any metric during training, validation, or testing using the `self.log()` method within the `LightningModule`.

# Example: Logging Validation Accuracy

```
class LightningCNNModel(pl.LightningModule):
    # Model definition here...

    def validation_step(self, batch, batch_idx):
        inputs, targets = batch
        outputs = self(inputs)
        loss = self.criterion(outputs, targets)

        # Calculate accuracy
        acc = (outputs.argmax(dim=1) == targets).float().mean()

        # Log accuracy
        self.log('val_accuracy', acc, prog_bar=True)

    return loss
```

In this example, the validation accuracy is calculated in the `validation_step()` method and logged using `self.log()`. The `prog_bar=True` argument ensures that the metric is displayed in the progress bar during training.

# Using Early Stopping

Early stopping is a critical technique for preventing overfitting, especially in deep-learning models. PyTorch Lightning includes an `EarlyStopping` callback that monitors a specified metric such as validation loss and halts training if the metric stops improving.

# Example: Early Stopping in PyTorch Lightning

```
early_stopping_callback =
pl.callbacks.EarlyStopping(monitor='val_loss', patience=3,
```