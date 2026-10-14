| Layer (type) | Output shape | Param # |
|---|---|---|
| LeakyReLU | (None, 8, 8, 64) | 0 |
| Flatten | (None, 4096) | 0 |
| Dense | (None, 128) | 524,416 |
| BatchNormalization | (None, 128) | 512 |
| LeakyReLU | (None, 128) | 0 |
| Dropout | (None, 128) | 0 |
| Dense | (None, 10) | 1290 |

Total params 592,554
Trainable params 591,914
Non-trainable params 640

![](bbox=[0.15, 0.35, 0.22, 0.43])

Before moving on, make sure you are able to calculate the output shape and number of parameters for each layer by hand. It's a good exercise to prove to yourself that you have fully understood how each layer is constructed and how it is connected to the preceding layer! Don't forget to include the bias weights that are included as part of the Conv2D and Dense layers.

# Training and Evaluating the CNN

We compile and train the model in exactly the same way as before and call the evaluate method to determine its accuracy on the holdout set (Figure 2-16).

```
model.evaluate(x_test, y_test, batch_size=1000)

10000/10000 [==============================] - 15s 1ms/step

[0.8423407137393951, 0.7155999958515167]
```

Figure 2-16. CNN performance

As you can see, this model is now achieving 71.5% accuracy, up from 49.0% previously. Much better! Figure 2-17 shows some predictions from our new convolutional model.

This improvement has been achieved simply by changing the architecture of the model to include convolutional, batch normalization, and dropout layers. Notice that the number of parameters is actually fewer in our new model than the previous model, even though the number of layers is far greater. This demonstrates the importance of being experimental with your model design and being comfortable with how the different layer types can be used to your advantage. When building generative