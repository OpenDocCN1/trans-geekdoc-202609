
# Deep Learning With TensorFlow

The next step is to feed the input data to the computational graph for the training process.

# Step 5: Training and Testing

Before starting the training process, define the method to evaluate the accuracy of mini-batches of data during the training. Then calculate the total accuracy score for the model.

Figure 44.

```python
correct_pred = tf.equal(tf.argmax(output_layer, 1), tf.argmax(Y, 1))
accuracy = tf.reduce_mean(tf.cast(correct_pred, tf.float32))
```

Now, initialize the session to run the graph.

Figure 45.

```python
init = tf.global_variables_initializer()
sess = tf.Session()
sess.run(init)
```

The main objective of the training process in deep learning is to optimize the loss function. Here, the authors are trying to minimize the difference between the predicted labels and the actual labels of the images. At each training step, parameters are adjusted in such a way that the loss is reduced for the next step (figure 46).

The output of the above lines of code is shown in figure 47.
Once training is done, run the session on the images. Now, the keep_prob dropout rate is 1.0 to ensure that all the units are active during the testing process (figure 48).

You can see that the accuracy of the above model is approximately equal to 92%. The proposed model can be tested on your hand-drawn number or any image of digit. One image can be downloaded from the given command (figure 49).

The above command will download the test image in the desired location.
Now, test the input image using below lines of code as seen in figure 50.

The output of the above code accurately determines that the given input image contains the image of digit 2.

Prediction for test image: 2

Figure 46.

```python
# train on mini batches
for i in range(n_iterations):
    batch_x, batch_y = mnist.train.next_batch(batch_size)
    sess.run(train_step, feed_dict={
        X: batch_x, Y: batch_y, keep_prob: dropout
    })

    # print Loss and accuracy (per minibatch)
    if i % 100 == 0:
        minibatch_loss, minibatch_accuracy = sess.run(
            [cross_entropy, accuracy],
            feed_dict={X: batch_x, Y: batch_y, keep_prob: 1.0}
        )
        print(
            "Iteration {}".format(str(i)),
            "\t Loss = {}".format(str(minibatch_loss)),
            "\t Accuracy = {}".format(str(minibatch_accuracy))
        )
```

Figure 47.

| Iteration | Loss | Accuracy |
|---|---|---|
| 0 | 3.563255 | 0.1328125 |
| 100 | 0.5562477 | 0.84375 |
| 200 | 0.2929745 | 0.8984375 |
| 300 | 0.2296962 | 0.9375 |
| 400 | 0.3628574 | 0.8828125 |
| 500 | 0.4162858 | 0.8828125 |
| 600 | 0.3385977 | 0.9140625 |
| 700 | 0.3483944 | 0.921875 |
| 800 | 0.2768194 | 0.929675 |
| 900 | 0.1626674 | 0.953125 |

Figure 48.

```python
test_accuracy = sess.run(accuracy, feed_dict={X: mnist.test.images, Y: mnist.test.labels, keep_prob: 1.0})
print("Accuracy on test set: %s", test_accuracy)
```

Accuracy on test set: 0.9179

Figure 49.

```bash
tensorflow-cpu C:\Users\anwar\Desktop\test_img.png
```

| % Total | % Verified | % Xfer | Average Speed | Time Total | Time Left | Current |
|---|---|---|---|---|---|---|
| 100 | 393 | 0 | 0:00:00 | 0:00:01 | 513 |

Figure 50.

```python
import numpy as np
from PIL import Image
img = np.array(Image.open("C:/Users/anwar/Desktop/test_img.png").convert('L'))
prediction = sess.run(tf.argmax(output_layer, 1), feed_dict={X: img})
print("Prediction for test image:", np.squeeze(prediction))
```

# ADVANTAGES AND DISADVANTAGES OF TENSORFLOW

### Advantages
- It is an open-source library so easily available free of cost.
- It provides graph visualizations using TensorBoard for a better understanding of the model.
- It supports both CPU and GPU.
- It has excellent community support.
- It provides regular updates and frequent releases with new features.
- Scalability.

### Disadvantages
- It not support windows operating system. If you are a window user, you can install it through anaconda or python package library.
- Extra steps are required to run a simple hello world program; we need to run the program using session.
- It supports only NVIDIA GPUs and has full language support of python.
- It has a unique structure so difficult to debug the program.

# REFERENCES
- Abadi, M., Agarwal, A., Barham, P., Chen, Z., Citro, C., Ghemawat, S. (2016). TensorFlow: Large-scale machine learning on distributed systems. arXiv preprint arXiv:1603.0467.
- Aryan, M. (2018). How to Use TensorBoard? Retrieved 12 September 2019, from https://itnext.io/how-to-use-tensorboard-5d82f08b65496
- Jason, B. (2019). What is Deep Learning? Retrieved 10 January 2020, from https://machinelearning-mastery.com/what-is-deep-learning/
- LeCun, Y., Cortes, C., & Burges, C. J. (1998). The MNIST database of handwritten digits. http://yann.lecun.com/exdb/mnist
- Ramsundar, B., & Zadeh, R. B. (2018). TensorFlow for deep learning: from linear regression to reinforcement learning. O'Reilly Media, Inc.
- TensorFlow. (2016). Retrieved 4 September 2019, from https://www.tensorflow.org/guide/graphs
- Zaccone, G., Karim, M. R., & Menshawy, A. (2017). Deep Learning with TensorFlow. Packt Publishing Ltd.

# Chapter 5
## Employee’s Attrition Prediction Using Machine Learning Approaches

Krishna Kumar Mohbey
https://orcid.org/0000-0002-7566-0703
Department of Computer Science, Central University of Rajasthan, India

# ABSTRACT
In any industry, attrition is a big problem, whether it is employee attrition of an organization or customer attrition of an e-commerce site. If we can accurately predict which customer or employee will leave their current company or organization, then it will save much time, effort, and cost of the employer and help them to hire or acquire substitutes in advance, and it would not create a problem in the ongoing process of an organization. In this chapter, a comparative analysis between various machine learning approaches such as Naive Bayes, SVM, decision tree, random forest, and logistic regression is presented. The presented result will help in identifying the behavior of employees who can be attained over the next time. Experimental results reveal that the logistic regression approach can reach up to 86% accuracy over other machine learning approaches.

# INTRODUCTION
Today attrition is one of the major problems faced by industry across the world. It is the most burning issue for the industry, and high attrition rates lead to many issues in the boundary of the organization like losing talents and knowledge, related to training and administration, and recruitment. It is observed that many attributes lead to the attrition of an employee which includes working environment, job satisfaction, employer’s behavior, job timing, and most important is salary or incentives. Also, the prediction model plays an essential role in finding the behavior of employees.

DOI: 10.4020/xxxx.xxxxxx

## Employee's Attrition Prediction Using Machine Learning Approaches
Today attrition is one of the major problems faced by industry across the world. It is the most burning issue for the industry, and high attrition rates lead to many issues in the boundary of the organization like losing talents and knowledge, related to training and administration, and recruitment. It is observed that many attributes lead to the attrition of an employee which includes working environment, job satisfaction, employer’s behavior, job timing, and most important is salary or incentives. Also, the prediction model plays an essential role in finding the behavior of employees.
