# Deep Learning Using Keras

Figure 23.

```
# evaluate model
scores = model.evaluate(x_test, y_test, verbose=1)
print('Test loss:', scores[0])
print('Test accuracy:', scores[1])
```

10000/10000 ======================================== 2s 232us/step
Test loss: 0.63431428062439
Test accuracy: 0.8589

Figure 24.

```
# evaluate model
scores = model.evaluate(x_test, y_test, verbose=1)
print('Test loss:', scores[0])
print('Test accuracy:', scores[1])
```

10000/10000 ======================================== 2s 236us/step
Test loss: 0.6355399031066
Test accuracy: 0.8398

Figure 25.

```
import keras
from matplotlib.pyplot import plt as plt
plt.plot(history.history['acc'])
plt.plot(history.history['val_acc'])
plt.title('model accuracy')
plt.xlabel('epoch')
plt.ylabel('accuracy')
plt.legend(['train', 'val'], loc='upper left')
plt.show()
```

```
plt.plot(history.history['loss'])
plt.plot(history.history['val_loss'])
plt.title('model loss')
plt.xlabel('epoch')
plt.ylabel('loss')
plt.legend(['train', 'val'], loc='upper left')
plt.show()
```

![](bbox=[0.135, 0.643, 0.803, 0.798])

54