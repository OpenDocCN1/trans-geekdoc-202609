# Deep Learning with Keras

# Step 5. Plotting the Loss and Accuracy

Figure 32.

```
```python
history_dict = history.history
loss_values = history_dict['loss']
val_values = history_dict['val_loss']
epochs = range(1, len(loss_values) + 1)
plt.figure(figsize=(14, 4))
plt.subplot(1,2,1)
plt.plot(epochs, loss_values, 'bo', label='Training Loss')
plt.plot(epochs, val_values, 'b', label='Validation Loss')
plt.title('Training and Validation Loss')
plt.xlabel('Epochs')
plt.legend()
acc = history_dict['val_acc']
epochs = range(1, len(acc) + 1)
plt.subplot(1,2,2)
plt.plot(epochs, acc, 'bo', label='Training Accuracy', c='orange')
plt.plot(epochs, val_acc, 'b', label='Validation Accuracy', c='orange')
plt.title('Training and Validation Accuracy')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend()
```
```

Figure 33.

![](bbox=[0.147, 0.563, 0.852, 0.735])

# TENSORFLOW VS. KERAS

TensorFlow and Keras are both framework in data science domain which included different libraries and inbuilt packages (Figure 1). TensorFlow is open source framework that is used basically in machine learning algorithm while Keras is neural network library written in python that work on top of TensorFlow. Keras is more user friendly, easy to use and debug and easy to extend for better and Keras provide more abstraction where TensorFlow is more flexible to modification. In terms of performance, keras is comparatively slower than TensorFlow.