When using InceptionV3's architecture, note that during the training loop, the model's output consists of the final output as well as an auxiliary output. The loss is computed for both outputs with the auxiliary loss typically being weighted to have less impact.

```
Epoch 1: Loss: 4.352704811888888
Epoch 2: Loss: 1.5783041149301602
Epoch 3: Loss: 1.0175445510450836
Epoch 4: Loss: 0.7405642401379393
Epoch 5: Loss: 0.5667243113793681
Epoch 6: Loss: 0.44321320430778177
Epoch 7: Loss: 0.3450072900489773
Epoch 8: Loss: 0.2725202218174477
Epoch 9: Loss: 0.218437113982561
Epoch 10: Loss: 0.17106323043727661
```

**Figure 8.5:** Output of training the Inception-v3 model on the CIFAR100 dataset for 10 epochs

# Evaluation Code

After the model has been trained, it's essential to evaluate its performance on a separate validation or test set to ensure it generalizes well to unseen data.

```
inceptionv3_pretrained.eval()  # Set the model to evaluation mode
correct = 0
total = 0
with torch.no_grad():
    for images, labels in test_loader:
        images, labels = images.to(device), labels.to(device)
        outputs, _ = inceptionv3_pretrained(images)  # Ignore auxiliary outputs during inference
        _, predicted = torch.max(outputs.data, 1)
        total += labels.size(0)
```