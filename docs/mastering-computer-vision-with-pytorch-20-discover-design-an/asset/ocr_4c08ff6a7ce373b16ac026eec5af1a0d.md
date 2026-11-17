```
```python
plt.xlim([0.0, 1.0])
plt.ylim([0.0, 1.05])
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('Receiver Operating Characteristic for CIFAR-10
classes')
plt.legend(loc="lower right")
plt.show()
# Confusion Matrix
conf_matrix = confusion_matrix(targets, predictions)
# Plot the confusion matrix as an image
fig, ax = plt.subplots(figsize=(10,10))
cax = ax.matshow(conf_matrix, cmap=plt.cm.Blues)
fig.colorbar(cax)
plt.xlabel('Predicted')
plt.ylabel('True')
plt.title('Confusion Matrix for CIFAR-10 Classification')
# Print the confusion matrix
tick_marks = np.arange(len(validation_set.classes))
plt.xticks(tick_marks, validation_set.classes, rotation=45)
plt.yticks(tick_marks, validation_set.classes)
plt.imshow(conf_matrix, interpolation='nearest',
cmap=plt.cm.Blues)
thresh = conf_matrix.max() / 2.
for i, j in product(range(conf_matrix.shape[0]),
range(conf_matrix.shape[1])):
plt.text(j, i, format(conf_matrix[i, j], 'd'),
horizontalalignment="center", color="white" if conf_matrix[i,
j] > thresh else "black")
plt.tight_layout()
plt.savefig('confusion_matrix.png') # Save the confusion
matrix as a image
plt.show()
```
```