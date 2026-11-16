# Box 8.1
Error Backpropagation

![](bbox=[0.16, 0.19, 0.82, 0.51])

Inputs to the backprop network are propagated feedforward: In the diagram above, the inputs on the left propagate forward through the connections (arrows) to the hidden layer of units, which in turn project to the output layer. The output is compared with the value given by a trainer, and the difference is used to update the weights to the output unit to reduce the error. The weights between the input units and the hidden layer are then updated based on backpropagating the error according to how much each weight contributes to the error. By training on many examples, the hidden units develop selective features that can be used to distinguish between different input patterns so that they can be separated into different categories in the output layer. This is called “representation learning.” Courtesy of Dr. Mahmoud.