in the above chunk is the categorical accuracy. In multiclass classification, the accuracy is defined as the average accuracy over all classes and all predictions. Since a prediction for one instance is a vector of weights, the ‘terminal’ prediction is the class that is associated with the largest weight. The accuracy then measures the proportion of times when the prediction is equal to the realized value (i.e., when the class is correctly guessed by the model).

Finally, we proceed with the training of the model.

```
fit_NN_C <- model_C %>% 
  fit(NN_train_features, 
      NN_train_labels_C, 
      epochs = 20, batch_size = 512, 
      validation_data = list(NN_test_features, 
                             NN_test_labels_C), 
    verbose = 0, 
    callbacks = list( 
      callback_early_stopping(monitor = "val_loss", 
                              min_delta = 0.001, 
                              patience = 3, 
                              verbose = 0 
                              ) 
          ) 
        )
plot(fit_NN_C)
```