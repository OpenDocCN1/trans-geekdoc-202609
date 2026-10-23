# 20.5 Training

Now that we have orchestrated all the pieces, we can start to train our model. When we create our learner we have to be careful of the inputs. As we are using one-channel images we need to adapt our learner (similar to what we did with the Bengali.AI dataset).

```
def alter_learner(learn, n_channels=1):
"Adjust a `Learner`'s model to accept `1` channel"
layer = learn.model[0][0]
layer.in_channels=n_channels
layer.weight = 
    nn.Parameter(layer.weight[:,1,:,:].unsqueeze(1))
learn.model[0][0] = layer
learn = Learner(dls,
    xresnet18(),
    CrossEntropyLossFlat(), metrics=accuracy)
```

Grab the input channels we have and pass them into our alter_learner-function.

n_c = dls.one_batch()[0].shape[1]; n_c 1 alter_learner(learn, n_c) Next we can find a learning-rate and train our learner for some epochs.

learn.lr_find() (0.09120108485221863, 0.002511886414140463)