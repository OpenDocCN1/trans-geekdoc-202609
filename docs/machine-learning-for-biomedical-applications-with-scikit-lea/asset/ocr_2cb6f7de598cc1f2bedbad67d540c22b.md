# Diagnosis of Heart Failure

![](bbox=[0.165, 0.092, 0.84, 0.29])

**Figure 9.6** Multinomial logistic regression as a single-layer perceptron. Left: the network diagram. The input features $x_i$, are passed through a linear layer composed of three neurons, for each class label. The outputs of the linear layer $z_k$ are passed through the softmax to convert them to the output class probabilities $\hat{p}_k$. Right: the result of a multi-label classification that predicts a 3-class heart failure diagnosis (healthy, moderate, and severe) from two cardiac imaging indices (EF and GLS), implemented in PyTorch as a network with a single linear layer, softmax, and the cross-entropy loss.

sample $i$. An example of one-hot encoding is shown here:

```
```
0 1 0 0
1 0 1 0
2 0 0 1
1 0 0 0
```
```

# ### 9.3.3 Linear multi-label classification in PyTorch

**Network architecture**

To implement a linear multi-label classifier in PyTorch, we need to create a class with one linear layer, with the number of output features equal to the number of labels. For example, to predict 3-class diagnosis of heart failure (healthy, mild, or severe) from two cardiac indices (EF and GLS), visualized in Fig. 9.6, right need a network composed of one linear layer with two input and three output features, which we can implement as:

```
```python
MultiLabelClassifier(nn.Module):
    def __init__(self):
        super(MultiLabelClassifier, self).__init__()
        self.layer = nn.Linear(2, 3)

    def forward(self, x):
        x = self.layer(x)
        return x
```
```