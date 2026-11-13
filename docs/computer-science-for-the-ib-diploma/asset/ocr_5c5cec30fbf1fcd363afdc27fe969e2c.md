```
# Convert grayscale pixels into floats with range [0...1]
x_train = x_train/255.0
x_test = x_test/255.0
# Convert the labels into "1 hot encoding" category arrays
# e.g. label of 3 becomes [0,0,0,1,0,0,0,0,0,0]
y_train = to_categorical(y_train)
y_test = to_categorical(y_test)
# Define the network, compile, and train it
model = models.Sequential([
    layers.Flatten(input_shape=(28,20)),
    layers.Dense(64, activation="relu", input_shape=(x_train.shape[1],)),
    layers.Dense(64, activation="relu"),
    layers.Dense(10, activation="sigmoid")
])
model.compile(optimizer="adam",
            loss="binary_crossentropy",
            metrics=["accuracy"])
history = model.fit(x_train, y_train, epochs=5)
# Run the unseen test data through the network to determine success
loss, accuracy = model.evaluate(x_test, y_test)
print(f"Accuracy: {accuracy}")
model.save("mnist-example.keras")
```

One step that may not be intuitively obvious is how to test this with your own data. Suppose you have a 28x28 grayscale PNG file you'd like to test on the ANN. The following is example code to do this task. (*By the way, ensure your image is white text on black background, as that is how the model has been trained.*)

```
**Python**
import numpy as np
from PIL import Image  # pip install Pillow
import tensorflow as tf
model = tf.keras.models.load_model("mnist-example.keras")
# Load the image file
image = Image.open("your image file.png")
image = image.convert("L")  # Grayscale to match the training data
image = image.resize((28, 28))  # Resize to match the training data
# Convert image to numpy array
image_array = np.array(image)
image_array = image_array/255.0  # Normalize to 0..1 scale
# Reshape the array for the model (Add a batch dimension at the beginning)
image_array = image_array.reshape(1, 28, 28)
# Send to the trained ANN
predictions = model.predict(image_array)
predicted_class = np.argmax(predictions, axis=1)
print("Predicted class:", predicted_class)
```