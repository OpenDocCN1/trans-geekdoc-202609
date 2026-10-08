```
```
120        # entries.
121        correct_count += torch.sum(
122            pred_labels == labels
123        ).item()
124    avg_test_loss = total_test_loss / len(mnist_test)
125    accuracy = correct_count / len(mnist_test)
126    return (avg_test_loss, accuracy)
127
128
129 # Initialize a list that holds the computed loss on every
130 # batch during training
131 train_losses = []
132
133 # Every 10 batches, we will compute the loss on the entire test
134 # set as well as the accuracy of the model's predictions on the
135 # entire test set. We do this for the purpose of illustrating in
136 # the produced plot the generalization capability of the ANN.
137 # Computing these losses and accuracies so frequently with such a
138 # relatively large set of datapoints (compared to the training
139 # set) is extremely computationally expensive, however (most of
140 # the training runtime will be spent computing these values) and
141 # so is not advisable during normal neural network training.
142 # Usually, the test set is only used at the very end to judge the
143 # performance of the final trained network. Often, a third set of
144 # datapoints, called the validation set (not used to train the
145 # network directly nor to evaluate it at the end) is used to
146 # judge overfitting or to tune hyperparameters.
147 test_interval = 10
148 test_losses = []
149 accuracies = []
150
151 # We run the training for 5 epochs, i.e., 5 full iterations
152 # through the training set.
153 i = 0
154 for e in range(5):
155     for images, labels in train_loader:
155         # Move the data to the device
156         images = images.to(device)
157         labels = labels.to(device)
158
159         # Zero out the gradients
160         optimizer.zero_grad()
161         # Compute the output of the neural network on the current
162         # minibatch
163         output = net(images)
164         # Compute the cross entropy loss
165         loss = loss_fn(output, labels)
166         # Compute the gradients
167         loss.backward()
168
```
```