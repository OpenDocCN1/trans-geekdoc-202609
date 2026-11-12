```
print("Baseline Error: %.2f%%" % (100-scores[1]*100))
```

# # Defining a Deep Model

Now, we will define a multi-layer convolution neural network in which we will add two hidden layers:

```
model = Sequential()
model.add(Conv2D(32, (3, 3), strides=(1, 1), padding = 'same' , input_shape = input_shape, activation = 'relu'))
model.add(Conv2D(32, (3, 3), strides=(1, 1), padding = 'same', activation = 'relu'))
model.add(MaxPooling2D((2, 2), strides=(2, 2), padding = 'valid'))
model.add(Conv2D(64, (3, 3), strides=(1, 1), padding = 'same', activation = 'relu'))
model.add(Conv2D(64, (3, 3), strides=(1, 1), padding = 'same', activation = 'relu'))
model.add(Flatten())
model.add(Dense(500, activation='relu'))
model.add(Dense(100, activation='relu'))
model.add(Dense(num_classes, activation='softmax'))
```

# # Analyzing Model Summary

```
model.summary()
import h5py
```

# # Compile model

```
model.compile(loss='categorical_crossentropy', optimizer='adam',
metrics=['accuracy'])
```

# # Training model

```
history = model.fit(X_train, y_train, validation_data=(X_val, y_val),
epochs=2, batch_size=200)
model.save_weights('CNN.h5')
```