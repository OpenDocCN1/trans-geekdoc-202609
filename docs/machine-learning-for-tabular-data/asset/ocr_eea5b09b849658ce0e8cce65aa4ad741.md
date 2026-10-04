# CHAPTER 3 Machine learning vs. deep learning

```
# define layers for continuous columns
for col in continuousscols:
    continuous(col) = Input(shape=[1], name=col)
    layers.append(continuous(col))
```

# Build layersor continuous
features

```
# build up layers

main_1 = concatenate([Dropout(dropout_rate), Flatten()(embeddings[collist[0]])]
dropout1(dropout_rate) = Flatten()(embeddings[collist[1]])
for col in collist:
    if (col == collist[0]) & (col == collist[1]):
        main_1 = concatenate([main_1, Dropout(dropout_rate), Flatten((embeddings[cols])])
```

```
if include_text:
    for col in texts:
        main_1 = concatenate([main_1, textembeddings[col]])
```

```
# for col in continuousscols:
main_1 = concatenate([main_1, continuous[col]])
```

```
# define output layer
output = Dense(1, activation=output_activation, main_1)
```

# Define
output layer

```
# define model
model = Model(inputlayer, output)
```

```
# define optimizer
optimizer = SGD(lr=learning_rate)
```

```
# compile model
model.compile(loss=loss_func, optimizer=optimizer, metrics=['"accuracy"])
weighted_metrics=['"accuracy"]
return model
```

# Compile
model

Figure 3.8 Model definition for the Keras deep learning solution for the Airbnb NYC problem (part 2)

![](bbox=[0.118, 0.563, 0.793, 0.843])

Interior layers

Input
layers

# Output
layer

Figure 3.9 Visualization of the Keras model for the Airbnb problem