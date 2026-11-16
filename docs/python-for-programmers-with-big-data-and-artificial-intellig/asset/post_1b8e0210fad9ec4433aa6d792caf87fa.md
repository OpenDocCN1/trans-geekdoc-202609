
Click here to view code image

```python
[47]: def display_probabilities(prediction):
    for index, probability in enumerate(prediction):
        print(f'{index}: {probability:.10%}')
```

Though the 8 (at index 495) in the first line of the image output looks like an 8, our model had trouble with it. As you can see in the following output, the model predicted this image as a 0, but also thought there was 16% chance it was a 6 and a 23% chance it was an 8:

Click here to view code image

```
[48]: display_probabilities(predictions[495])
0: 59.7235262394%
1: 0.0000015465%
2: 0.8047289215%
3: 0.0001740813%
4: 0.0016636326%
5: 0.0030567855%
6: 16.1390662193%
7: 0.0000001781%
8: 23.3022540808%
9: 0.0255270657%
```

The 2 (at index 583) in the first row was predicted to be a 7 with 62.7% certainty, but the model also thought there was a 36.4% chance it was a 2:

Click here to view code image

```
[49]: display_probabilities(predictions[583])
0: 0.0000003016%
1: 0.0000005715%
2: 36.4056706429%
3: 0.0176281916%
4: 0.0000561930%
5: 0.0000000003%
6: 0.0000000019%
7: 62.7455413342%
8: 0.8310816251%
9: 0.0000114385%
```

The 6 (at index 625) at the beginning of the second row was predicted to be a 4, though that was far from certain. In this case, the probability of a 4 (51.6%) was only slightly higher than the probability of a 6 (48.38%):

Click here to view code image

```
[50]: display_probabilities(predictions[625])
0: 0.0008245181%
1: 0.0000041209%
2: 0.0012774357%
3: 0.0000000009%
4: 51.6223073006%
5: 0.0000001779%
6: 48.3754962683%
7: 0.000000085%
8: 0.0000048182%
9: 0.0000785786%
```

## 15.6.6 Saving and Loading a Model

Neural network models can require significant training time. Once you’ve designed and tested a model that suits your needs, you can save its state. This allows you to load it later to make more predictions. Sometimes models are loaded and further trained for new problems. For example, layers in our model already know how to recognize features such as lines and curves, which could be useful in handwritten character recognition (as in the EMNIST dataset) as well. So you could potentially load the existing model and use it as the basis for a more robust model. This process is called **transfer learning** <sup>5</sup> <sup>6</sup>—you transfer an existing model’s knowledge into a new model. A Keras model’s **save method** stores the model’s architecture and state information in a format called **Hierarchical Data Format (HDF5)**. Such files use the `.h5` file extension by default:

<sup>5</sup> https://towardsdatascience.com/transfer-learning-from-pre-trained-models-f2393f124751.

<sup>6</sup> https://medium.com/nanonets/nanonets-how-to-use-deep-learning-when-you-have-limited-data-f68c0b512cab.

```
[51]: cnn.save('mnist_cnn.h5')
```

You can load a saved model with the `load_model` function from the `tensorflow.keras.models` module:

Click here to view code image

```python
from tensorflow.keras.models import load_model
cnn = load_model('mnist_cnn.h5')
```

You can then invoke its methods. For example, if you’ve acquired more data, you could call `predict` to make additional predictions on new data, or you could call `fit` to start training with the additional data.

Keras provides several additional functions that enable you to save and load various aspects of your models. For more information, see

https://keras.io/getting-started/faq/#how-can-i-save-a-keras-model

## 15.7 VISUALIZING NEURAL NETWORK TRAINING WITH TENSORBOARD

With deep learning networks, there’s so much complexity and so much going on internally that’s hidden from you that it’s difficult to know and fully understand all the details. This creates challenges in testing, debugging and updating models and algorithms. Deep learning learns the features but there may be enormous numbers of them, and they may not be apparent to you.

Google provides the TensorBoard 7, 8 tool for visualizing neural networks implemented in TensorFlow and Keras. Just as a car's dashboard visualizes data from your car's sensors, such as your speed, engine temperature and the amount of gas remaining, a TensorBoard dashboard visualizes data from a deep learning model that can give you insights into how well your model is learning and potentially help you tune its hyperparameters. Here, we'll introduce TensorBoard.

7 https://github.com/tensorflow/tensorboard/blob/master/README.md.

8 https://www.tensorflow.org/guide/summaries_and_tensorboard.

### Executing TensorBoard

TensorBoard monitors a folder on your system looking for files containing the data it will visualize in a web browser. Here, you'll create that folder, execute the TensorBoard server, then access it via a web browser. Perform the following steps:

- 1. Change to the ch15 folder in your Terminal, shell or Anaconda Command Prompt.

- 2. Ensure that your custom Anaconda environment tf_env is activated:

```
conda activate tf_env
```

- 3. Execute the following command to create a subfolder named logs in which your deep-learning models will write the information that TensorBoard will visualize:

```
mkdir logs
```

- 4. Execute TensorBoard

```
tensorboard --logdir=logs
```

- 5. You can now access TensorBoard in your web browser at

```
http://localhost:6006
```

If you connect to TensorBoard before executing any models, it will initially display a page indicating “No dashboards are active for the current data set.” 9

- 9 TensorBoard does not currently work with Microsoft's Edge browser.

### The TensorBoard Dashboard

TensorBoard monitors the folder you specified looking for files output by the model during training. When TensorBoard sees updates, it loads the data into the dashboard:

![](img/34b7fc2f1ee27beb73bca14927d42340_709_0.png)

You can view the data as you train or after training completes. The dashboard above shows the TensorBoard **SCALARS** tab, which displays charts for individual values that change over time, such as the training accuracy (acc) and training loss (loss) shown in the first row, and the validation accuracy (val_acc) and validation_loss (val_loss) shown in the second row. The diagrams visualize a 10-epoch run of our MNIST convnet, which we provided in the notebook MNIST_CNN_TensorBoard.ipynb. The epochs are displayed along the x-axes starting from 0 for the first epoch. The accuracy and loss values are displayed on the y-axes. Looking at the training and validation accuracies, you can see in the first 5 epochs similar results to the five-epoch run in the previous section.

For the 10-epoch run, the training accuracy continued to improve through the 9th epoch, then decreased slightly. This might be the point at which we're starting to overfit, but we might need to train longer to find out. For the validation accuracy, you can see that it jumped up quickly, then was relatively flat for five epochs before jumping up then decreasing. For the training loss, you can see that it drops quickly, then continuously declines through the ninth epoch, before a slight increase. The validation loss dropped quickly then bounced around. We could run this model for more epochs to see whether results improve, but based on these diagrams, it appears that around the sixth epoch we get a nice combination of training and validation accuracy with minimal validation loss.

Normally these diagrams are stacked vertically in the dashboard. We used the search field (above the diagrams) to show any that had the name “mnist” in their folder name—we’ll configure that in a moment. TensorBoard can load data from multiple models at once and you can choose which to visualize. This makes it easy to compare several different models or multiple runs of the same model.

### Copy the MNIST Convnet's Notebook

To create the new notebook for this example:

- 1. Right-click the MNIST_CNN.ipynb notebook in JupyterLab’s File Browser tab and select Duplicate to make a copy of the notebook.
