![](bbox=[0.23, 0.06, 0.77, 0.42])

# FIGURE 7.10: Output from a trained recurrent neural network (regression task).

Compared to our previous models, the major difference both in the ouptut (the graph on Figure 7.10) and the input (the code) is the absence of validation (or testing) data. One reason for that is because Keras is very restrictive on RNNs and imposes that both the training and testing samples share the same dimensions. In our situation this is obviously not the case, hence we must bypass this obstacle by duplicating the model.

```
new_model <- keras_model_sequential() %>%
  layer_gru(units = 16,
            batch_input_shape = c(nb_stocks,
                                  nb_dates_test,
                                  nb_feats),
            activation = 'tanh',
            return_sequences = TRUE) %>%  # New dimensions
  # Activation function
  # Return the full sequence
layer_dense(units = 1)  # Output dimension
new_model %>% keras::set_weights(keras::get_weights(model_RNN))
```

Finally, once the new model is ready, and with the matching dimensions, we can push forward to predicting the test values. We resort to the predict() function and immediately compute the hit ratio obtained by the model.

```
pred_rnn <- predict(new_model, test_features_rnn, batch_size = nb_stocks) # Predictions
mean(c(t(as.matrix(pred_rnn))) * test_labels_rnn > 0) # Hit ratio
```

```
## [1] 0.4995844
```

The hit ratio is close to 50%, hence the model does hardly better than coin tossing.

Before we close this section on RNNs, we mention a new type architecture, called α-RNN which are simpler compared to LSTMs and GRUs. They consist in vanilla RNNs to which a