might have a high _variance_ with regard to the validation split. This would prevent us
from reliably evaluating our model.

The best practice in such situations is to use _K-fold_ cross-validation (see figure 4.8).

![](bbox=[0.166, 0.16, 0.77, 0.365])

# Figure 4.8 K-fold cross-validation with K=3

It consists of splitting the available data into _K_ partitions (typically _K_ = 4 or 5), instanti-
ating _K_ identical models, and training each one on _K_ – 1 partitions while evaluating
on the remaining partition. The validation score for the model used is then the aver-
age of the _K_ validation scores obtained. In terms of code, this is straightforward.

```
Listing 4.26 K-fold validation

k = 4
num_val_samples = len(train_data) // k
num_epochs = 100
all_scores = []
for i in range(k):
    print(f"Processing fold #{i}")
    val_data = train_data[i * num_val_samples: (i + 1) * num_val_samples]
    val_targets = train_targets[i * num_val_samples: (i + 1) * num_val_samples]
    partial_train_data = np.concatenate(
        [train_data[:i * num_val_samples],
         train_data[(i + 1) * num_val_samples:]],
        axis=0)
    partial_train_targets = np.concatenate(
        [train_targets[:i * num_val_samples],
         train_targets[(i + 1) * num_val_samples:]],
        axis=0)
    model = build_model()
    model.fit(partial_train_data, partial_train_targets,
              epochs=num_epochs, batch_size=16, verbose=0)
    val_mse, val_mae = model.evaluate(val_data, val_targets, verbose=0)
    all_scores.append(val_mae)
```