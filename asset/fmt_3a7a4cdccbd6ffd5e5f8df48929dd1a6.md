
```python
def load_all_models(n_models):
    all_models = list()

    for i in range(n_models):
        # define filename for this ensemble
        filename = 'models/model_' + str(i + 1) + '.h5'

        # load model from file
        model = load_model(filename)

        # add to list of members
        all_models.append(model)

        print('>loaded %s' % filename)

    return all_models


# create stacked model input dataset as outputs from the ensemble
def stacked_dataset(members, inputX):
    stackX = None

    for model in members:
        # make prediction
        yhat = model.predict(inputX, verbose=0)

        # stack predictions into [rows, members, probabilities]
        if stackX is None:
            stackX = yhat
        else:
            stackX = dstack((stackX, yhat))

    # flatten predictions to [rows, members x probabilities]
    stackX = stackX.reshape((stackX.shape[0], stackX.shape[1] * stackX.shape[2]))

    return stackX


# fit a model based on the outputs from the ensemble
def fit_stacked_model(members, inputX, inputy):
    # create dataset using ensemble
    stackedX = stacked_dataset(members, inputX)

    # fit standalone model
    model = LogisticRegression(solver='lbfgs', multi_class='multinomial')

    model.fit(stackedX, inputy)

    return model


# make a prediction with the stacked model
def stacked_prediction(members, model, inputX):
    # create dataset using ensemble
    stackedX = stacked_dataset(members, inputX)

    # make a prediction
    yhat = model.predict(stackedX)

    return yhat


# generate 2d classification dataset
X, y = make_blobs(
    n_samples=1100,
    centers=3,
    n_features=2,
    cluster_std=2,
    random_state=2
)

# split into train and test
n_train = 100

trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
```

```python
# load all models
n_members = 5

members = load_all_models(n_members)

print('Loaded %d models' % len(members))

# evaluate standalone models on test dataset
for model in members:
    testy_enc = to_categorical(testy)

    _, acc = model.evaluate(testX, testy_enc, verbose=0)

    print('Model Accuracy: %.3f' % acc)

# fit stacked model using the ensemble
model = fit_stacked_model(members, testX, testy)

# evaluate model on test set
yhat = stacked_prediction(members, model, testX)

acc = accuracy_score(testy, yhat)

print('Stacked Test Accuracy: %.3f' % acc)
```

清单25.23：拟合逻辑回归堆叠模型的示例。

运行示例时，首先将子模型加载到一个列表中，并评估每个模型的性能。我们可以看到，表现最好的模型是最后一个模型，准确率约为81.3%。

注意：鉴于学习算法的随机性，您的具体结果可能会有所不同。请考虑多次运行该示例，并比较平均性能。

```text
>loaded models/model_1.h5
>loaded models/model_2.h5
>loaded models/model_3.h5
>loaded models/model_4.h5
>loaded models/model_5.h5

Loaded 5 models

Model Accuracy: 0.805
Model Accuracy: 0.806
Model Accuracy: 0.804
Model Accuracy: 0.809
Model Accuracy: 0.813
```

清单25.24：加载并评估独立MLP模型的示例输出。

接下来，在测试集上使用每个子模型预测的概率训练一个逻辑回归元学习器，然后在测试集上评估整个堆叠模型。在这种情况下，我们可以看到元学习器在测试集上的表现优于每个子模型，达到了约82.4%的准确率。

```text
Stacked Test Accuracy: 0.824
```

清单25.25：评估堆叠模型的示例输出。

## 25.2.5 集成堆叠模型

当使用神经网络作为子模型时，可能希望使用神经网络作为元学习器。具体来说，子网络可以嵌入到一个更大的多头神经网络中，该网络学习如何最佳地组合每个输入子模型的预测。这使得堆叠集成可以被视为一个单一的大型模型。

这种方法的好处是子模型的输出直接提供给元学习器。此外，如果希望的话，也可以结合元学习器模型来更新子模型的权重。这可以通过使用Keras函数式接口来开发模型实现。

```python
# update all layers in all models to not be trainable
for i in range(len(members)):
    model = members[i]

    for layer in model.layers:
        # make not trainable
        layer.trainable = False

        # rename to avoid 'unique layer name' issue
        layer.name = 'ensemble_' + str(i + 1) + '_' + layer.name
```

清单25.26：更新层名称并将层设置为不可训练的示例。

一旦子模型准备好，我们就可以定义堆叠集成模型。每个子模型的输入层将作为这个新模型的独立输入头。这意味着必须向模型提供任何输入数据的`k`份副本，其中`k`是输入模型的数量，在本例中为5。

然后可以合并每个模型的输出。在这种情况下，我们将使用简单的连接合并，将从5个模型中的每一个预测的三个类别概率创建一个15元素向量。然后，我们将定义一个隐藏层来解释元学习器的这个`输入`，以及一个输出层，该输出层将做出自己的概率预测。

下面的`define_stacked_model()`函数实现了这一点，并在给定一组训练好的子模型时返回一个堆叠泛化神经网络模型。

```python
# define stacked model from multiple member input models
def define_stacked_model(members):
    # update all layers in all models to not be trainable
    for i in range(len(members)):
        model = members[i]

        for layer in model.layers:
            # make not trainable
            layer.trainable = False

            # rename to avoid 'unique layer name' issue
            layer.name = 'ensemble_' + str(i + 1) + '_' + layer.name

    # define multi-headed input
    ensemble_visible = [model.input for model in members]

    # concatenate merge output from each model
    ensemble_outputs = [model.output for model in members]

    merge = concatenate(ensemble_outputs)

    hidden = Dense(10, activation='relu')(merge)
    output = Dense(3, activation='softmax')(hidden)

    model = Model(inputs=ensemble_visible, outputs=output)

    # plot graph of ensemble
    plot_model(model, show_shapes=True, to_file='model_graph.png')

    # compile
    model.compile(
        loss='categorical_crossentropy',
        optimizer='adam',
        metrics=['accuracy']
    )

    return model
```

清单25.27：用于定义堆叠MLP模型的函数示例。

调用此函数时会生成网络图，以便了解集成模型的组合方式。

```python
# define ensemble model
stacked_model = define_stacked_model(members)
```

清单25.28：定义堆叠MLP模型的示例。

生成该图需要安装`pygraphviz`。如果在您的工作站上安装有困难，可以注释掉对`plot_model()`函数的调用。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_531_0.png)

图25.3：神经网络模型堆叠泛化集成的可视化。

一旦模型定义完成，就可以进行拟合。我们可以直接在保留测试数据集上拟合它。由于子模型不可训练，它们的权重在训练期间不会更新，只有新的隐藏层和输出层的权重会被更新。

下面的`fit_stacked_model()`函数将拟合堆叠神经网络模型达300个周期。

```python
# fit a stacked model
def fit_stacked_model(model, inputX, inputy):
    # prepare input data
    X = [inputX for _ in range(len(model.input))]

    # encode output data
    inputy_enc = to_categorical(inputy)

    # fit model
    model.fit(X, inputy_enc, epochs=300, verbose=0)
```

清单25.29：用于拟合堆叠MLP模型的函数示例。

我们可以调用此函数，传入已定义的堆叠模型和测试数据集。

```python
# fit stacked model on test dataset
fit_stacked_model(stacked_model, testX, testy)
```

清单25.30：拟合堆叠MLP模型的示例。

拟合完成后，我们可以使用新的堆叠模型对新数据进行预测。这就像在模型上调用`predict()`函数一样简单。一个小的改动是，我们需要向模型提供一个包含`k`份输入数据的列表，每份对应`k`个子模型。

下面的`predict_stacked_model()`函数简化了使用堆叠模型进行预测的过程。

```python
# make a prediction with a stacked model
def predict_stacked_model(model, inputX):
    # prepare input data
    X = [inputX for _ in range(len(model.input))]

    # make prediction
    return model.predict(X, verbose=0)
```

清单25.31：用于使用堆叠MLP模型进行预测的函数的示例。

我们可以调用此函数为测试数据集进行预测并报告准确率。我们期望神经网络学习器的性能优于任何单个子模型，并且可能与上一节中使用的线性元学习器具有竞争力。

```python
# make predictions and evaluate
yhat = predict_stacked_model(stacked_model, testX)

yhat = argmax(yhat, axis=1)

acc = accuracy_score(testy, yhat)

print('Stacked Test Accuracy: %.3f' % acc)
```

清单25.32：使用堆叠MLP模型进行预测的示例。

将所有这些元素结合起来，完整示例如下所示。

```python
# stacked generalization with neural net meta model on blobs dataset
from sklearn.datasets.samples_generator import make_blobs
from sklearn.metrics import accuracy_score

from keras.models import load_model
from keras.utils import to_categorical
from keras.utils import plot_model
from keras.models import Model
from keras.layers import Dense
from keras.layers.merge import concatenate

from numpy import argmax


# load models from file
def load_all_models(n_models):
    all_models = list()

    for i in range(n_models):
        # define filename for this ensemble
        filename = 'models/model_' + str(i + 1) + '.h5'

        # load model from file
        model = load_model(filename)

        # add to list of members
        all_models.append(model)

        print('>loaded %s' % filename)

    return all_models


# define stacked model from multiple member input models
def define_stacked_model(members):
    # update all layers in all models to not be trainable
    for i in range(len(members)):
        model = members[i]

        for layer in model.layers:
            # make not trainable
            layer.trainable = False

            # rename to avoid 'unique layer name' issue
            layer.name = 'ensemble_' + str(i + 1) + '_' + layer.name

    # define multi-headed input
```
