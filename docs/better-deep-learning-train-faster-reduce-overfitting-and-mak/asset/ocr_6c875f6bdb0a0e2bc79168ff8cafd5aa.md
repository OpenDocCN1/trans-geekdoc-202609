# 23.2 Horizontal Voting Ensembles Case Study

```
if i >= n_save_after:
    model.save('models/model_' + str(i) + '.h5')
```

Listing 23.14: Example of saving horizontal ensemble members to file.

Running the example creates the models/ folder and saves 50 models into the directory. Note, to re-run this example, you must delete the models/ directory so that the script can recreate it.

# 23.2.4 Make Horizontal Ensemble Predictions

Now that we have created the models, we can use them in a horizontal voting ensemble. First, we need to load the models into memory. This is reasonable as the models are small. If you are trying to develop a horizontal voting ensemble with very large models, it might be easier to load models one at a time, make a prediction, then load the next model and repeat the process. The function load_all_models() below will load models from the models/ directory. It takes the start and end epochs as arguments so that you can experiment with different groups of models saved over contiguous epochs.

```
# load models from file
def load_all_models(n_start, n_end):
    all_models = list()
    for epoch in range(n_start, n_end):
        # define filename for this ensemble
        filename = 'models/model_' + str(epoch) + '.h5'
        # load model from file
        model = load_model(filename)
        # add to list of members
        all_models.append(model)
        print('>loaded %s' % filename)
    return all_models
```

Listing 23.15: Example of a function for loading saved ensemble members.

We can call the function to load all of the models. We can then reverse the list of models so that the models at the end of the run are at the beginning of the list. This will be helpful later when we test voting ensembles of different sizes, including models sequentially from the end of the run backward through training epochs, in case the best models really were at the end of the run.

```
# load models in order
members = load_all_models(950, 1000)
print('Loaded %d models' % len(members))
# reverse loaded models so we build the ensemble with the last models first
members = list(reversed(members))
```

Listing 23.16: Example of a loading saved ensemble members.

Next, we can evaluate each saved model on the test dataset, as well as a voting ensemble of the last n contiguous models from training. We want to know how well each model actually performed on the test dataset and, importantly, the distribution of model performance on the test dataset, so that we know how well (or poorly) an average model chosen from the end of the run would perform in practice. We don't know how many members to include in the horizontal