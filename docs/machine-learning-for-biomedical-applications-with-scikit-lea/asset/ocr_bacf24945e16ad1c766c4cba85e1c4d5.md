type so that we can apply the forward pass that predicts the logits z. Note that logits can take both positive and negative values. After we pass them through softmax, we obtain class probabilities p, which are between 0 and 1 and add up to 1. The predicted label y corresponds to the class with the highest probability:

```
# create feature vector
x = torch.tensor((0,0)).reshape(1,2).float(0)
print('Input x: ', x)
# predict logits
z = net(x)
print('Logits z: ', z.data)
# probabilities
p=torch.nn.functional.softmax(z,dim=1)
print('Probabilities p: ', p.data)
# labels
y = torch.argmax(z, dim=1)
print('Label y: ', y)
>>> Input x: tensor([[0., 0.]])
>>> Logits z: tensor([[0.18, 1.30, -2.30]])
>>> Probabilities p: tensor([[0.24, 0.74, 0.02]])
>>> Label y: tensor([1])
```

# Evaluating performance

PyTorch does not provide functionality for evaluating the performance of the models. We therefore have to implement it or use another package, such as scikit-learn. Here we show how to implement calculation of accuracy. We will perform forward pass to obtain predicted logits and calculate the predicted labels y_pred. The accuracy can be easily evaluated by comparing predicted and true labels, converting the logical values to float and calculating the mean value:

```
pred=net(X)
y_pred = torch.argmax(pred, dim=1)
accuracy = (y_pred==y).float().mean()
print(accuracy)
>>> tensor(0.91))
```

Of course, we need to evaluate the accuracy on training and validation sets to monitor training, and after the model is trained, we calculate the final performance on the test set that was completely excluded from the training. We will provide full details through a real-world example in Sect. 10.3.