```
seq_cluster(cont_bn, block3), seq_cluster(full_lin, block4)]
fcc = seq_cluster(lin_bn_drop, block5)
g = graph_items(*model)
g.add_items(fcc)
g.add_items(*object_connections(conns))
```

Now we can print the visualization for our model by just calling g. g

We see that our input is first pre-processed and then passed to an Embedding Matrix (for categorical data) or to a BatchNorm layer for continuous data. Afterwards it goes through the 3 fully connected linear layers.

This is what the fastai tabular model basically looks like. It is a very lean model (compared to the fast_tab model). Let’s analyze and compare the TabNet Model!

![](bbox=[0.11, 0.44, 0.92, 0.58])

The head of the model is the same as with the fastai model. We start by pre-processing and passing the data either to the categorical embeddings or the batch normalization. Afterwards the outputs are concatenated and fed into TabNet. The TabNet model consists of an Attention Transformer, a Feature Transformer and a Mapping (Linear)Layer. We get 4 outputs: Output, Mask_Loss, Mask_Explain and Masks. TabNet operates by putting a mask onto the values. This allows the model to inspect which values affected the output.

Let’s first look at the Feature Transformer: