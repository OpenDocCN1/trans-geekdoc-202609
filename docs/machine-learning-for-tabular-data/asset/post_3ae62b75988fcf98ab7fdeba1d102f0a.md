
## CHAPTER 3 Machine learning vs. deep learning

```python
list_of_lists_test.append(X_test[i].tolist())
# convert lists of lists to numpy arrays of lists
xgb_X_train = np.array(list_of_lists_train).T
xgb_X_test = np.array(list_of_lists_test).T
```

Converts the test list of lists into a numpy array

Note that this is a example of the XGBoost code having additional complexity compared to the Keras code, this additional code is not intrinsically required by XGBoost but rather because of the fact that the XGBoost solution was adapted from the Keras solution.

To get additional confirmation of what the XGBoost data preparation code does, to Gemini (https://gemini.google.com) and paste the code into the entry field along with the prompt "what does this code do" and click the Submit button, as shown in figure 3.6.

![](img/def89cc476fa39f4c54bd34e78d91674_92_0.png)

**Figure 3.6 Entering a request to interpret code in Gemini**

You will get a response that explains what the code does with this summary:

In essence, the code does the following:
- It extracts specific elements from two input lists (X_train_list and X_test_list),
- It arranges these elements into a specific format (lists of lists).
- It converts these lists into NumPy arrays,
- preparing the data for further processing or model training.

Now that we have looked at the difference between XGBoost and Keras in terms of data preparation, let's compare the model definition code for the two solutions.

The following is the XGBoost model definition for the Airbnb NYC problem—one line of code that follows the pattern of Scikit-learn:

```python
model = XGBClassifier()
```

## Predicting Airbnb prices in New York City

Let's look at what the model definition code looks like for the Keras solution. Figure 3.7 shows the initial part of the function that defines the deep learning model for the Airbnb NYC problem.

```python
def keras_model():
    # define Keras model by specifying layers by column type
    Returns:
        model: Keras model with the layers specified by the structure of the dataset

    catinputs = [] # list of categorical inputs
    textinputs = [] # list of text inputs
    continputs = [] # list of continuous inputs
    textembeddings = []
    catemb = 10 # size of categorical embeddings
    textemb = 50 # size of text embeddings

    collistx = []
    textlayerlist = []
    inputlayer = []
    print("textname", textmax)
    # define layers for categorical columns
    for col in collistx:
        catinput[col] = Input(shape=[1], name=col)
        inputlayer.append(catinput[col])
        print("inputname", inputname)
        embeddings[col] = Embedding(max(dict[col]), catemb)(catinput[col])
        # batchnorm all
        embeddings[col] = BatchNormalization()(embeddings[col])
        collistx.append(embeddings[col])
    # define layers for text columns
    if includetext:
        for col in textcol:
            textinputs[col] = Input(shape=X_train[col], shape[1], name=col)
            print("input shape", X_train[col], shape[1])
            inputlayer.append(textinputs[col])
            embeddings[col] = Embedding(max(dict[col]), textemb)(textinputs[col])
            textembeddings[col] = Dense(64, activation='relu')(embeddings[col])
            textembeddings[col] = Dropout(rate=0.2)(GRU(16,kernel_regularizer=l2(0.2_lambda)))(textembeddings[col])
            collistx.append(textembeddings[col])
        print("max in the midst", np.max(np.max(train[col].max), np.max(test[col].max)) + 10)
    # through loops for col
```

![](img/def89cc476fa39f4c54bd34e78d91674_93_0.png)

![](img/def89cc476fa39f4c54bd34e78d91674_93_1.png)

![](img/def89cc476fa39f4c54bd34e78d91674_93_2.png)

Figure 3.7 Model the Keras definition for learning the deep learning model for the Airbnb part (1)

Figure 3.8 shows the rest of the function that defines the deep learning model for the Airbnb NYC problem.
Figure 3.9 shows the visualization for the model for the Airbnb problem.
This is a bit of extreme—the deep model definition could have been defined more simply. This model definition specifies a different set of Keras layers for each column type (continuous, categorical, and text). This is not the minimal layer possible for a tabular data, but it is very flexible. It will be able to deal with datasets with various combinations of continuous, categorical, and text columns. Also, this model definition includes code that specifies the layers for text

## CHAPTER 3 Machine learning vs. deep learning

```python
# define layers for continuous columns
for col in continuousscols:
    continuous[col] = Input(shape=[1], name=col)
    layers.append(continuous[col])
```

## Build layers for continuous features

```python
# build up layers
main_1 = concatenate([Dropout(dropout_rate), Flatten()(embeddings[collist[0]])])
dropout1(dropout_rate) = Flatten()(embeddings[collist[1]])
for col in collist:
    if (col == collist[0]) & (col == collist[1]):
        main_1 = concatenate([main_1, Dropout(dropout_rate), Flatten(embeddings[cols])])
```

```python
if include_text:
    for col in texts:
        main_1 = concatenate([main_1, textembeddings[col]])
```

```python
# for col in continuousscols:
main_1 = concatenate([main_1, continuous[col]])
```

```python
# define output layer
output = Dense(1, activation=output_activation, main_1)
```

## Define output layer

```python
# define model
model = Model(inputlayer, output)
```

```python
# define optimizer
optimizer = SGD(lr=learning_rate)
```

```python
# compile model
model.compile(loss=loss_func, optimizer=optimizer, metrics=['accuracy'])
return model
```

## Compile

Figure 3.8 Model definition for Keras solution for Airbnb NYC problem (part 2)

![](img/def89cc476fa39f4c54bd34e78d91674_94_0.png)

Interior layers

Input layers

## Output

Figure 3.9 Visualization of the model for the Airbnb problem
