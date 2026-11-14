Then we used Gaussian noise injection (from Keras package) of 0.05 to introduce some noise (Figure S1) to reduce overfitting because this will force the NN to learn the true parameters even though the SFS is slightly distorted (or noisy). We used logcosh as a loss function and Nadam for the optimizer (both from Keras package). Although we have used other more classical approaches (i.e., mean square error, stochastic gradient descent, etc.), we found this combination to be better suited for our approach.

We used two hidden layers of the dense NN with the activation relu (Figure S1). We used the softmax layer (from Keras package) for the output layer with the same number of units as the number of trained models. We added the masking layer and a noise injection layer as above. We used a 1% dropout layer (from Keras package) within every dense layer to make it more robust. We used categorical_crossentropy for the loss function and adam for the optimizer (both from Keras package).

The NN ran through the training dataset several times (epochs) to increase accuracy. We used EarlyStopping (from Keras package) on loss coming from validation dataset with the patient of 100. This stopped the epoch cycle in case there was no improvement for the last 100 epochs (meaning the NN reached a convergence for the current data). We used the ModelCheckpoint (from Keras package) of the lowest loss result on validation data, as the last epoch is not guaranteed to have the lowest loss on validation data. We also used ReduceLROnPlateau (from Keras package) of factor 0.2 to reduce the learning rate if we reached minima for several epochs (ten by default). Learning rate too low at the start makes the NN learn slow, but in the later stage, high learning rate performs worse than lower learning rate.

After the training was done, we used the testing dataset to predict models from the simulated SFS, which we then used to perform the cross-validation test by using ABC with the tolerance of 0.033 (which converts to 100 samples) in case of three models and 0.0066 (which converts to 100 samples) in case of 15 models via rejection (from abc package). We applied the model selection by abc-postpr (from abc package) to the real data. See a schematic representation in Figure S2.

After training is done, we used the testing dataset to predict the parameter from the SFS, which was then used for cross-validation tests and parameter prediction via loclinear from ABC^58 with the tolerance of 0.01. The whole approach is presented in a flowchart (Figure S2).

# **Model selection with DL**

# **ABC-DLS**

Our implementation of the ABC-DL method was further improved by using the SMC approach,^36 which opens up a new way to make inferences for similar cases (here onward, we call this implementation DLS). Although SMC has lots of different implementation and can be quite complex, we used a simpler version of SMC here. In our implementation, we only selected the top 5% of best samples coming from every cycle of ABC and discarded the rest. The ranges of the parameter values were estimated from these top samples and new samples were drawn from the uniform distributions for these new posterior ranges. To introduce mutations in the algorithm, we increased the posterior range by 1% in every cycle. As a result, the simulated SFS, which is used as input for the NN, becomes more and more similar to real or observed SFS with every iteration of the algorithm.

Here, we describe model selection by using NN and ABC. Unless stated otherwise, we simulated 2,000 simulations for each of the three demographic models tested (see full description of demographic models below). We simulated all the models for 3 Gb regions to make it equal for different approaches and finally scale the real data accordingly. This approach is preferable because we can train the NN only once for different length of real data. To test whether our scaling approach and the length of simulated region are not creating any biases, we also simulated an only 647 Mb region (equal to our filtering strategy 1) with the multiple of 25 Kb regions without using scaling in Table S4. The resulting CSV files (one per model) are used together as input for model selection. Model selection was repeated ten times both for DL and DLS. We found that if the results have high accuracy (posterior probability on observed data is >95% for the correct model), all the ten runs are essentially equal (which is expected).

# **Parameter estimation with DLS**

This method uses the standard parameter estimation strategy of DL (described above) together with the modified SMC algorithm used for recursion.

For parameter estimation, we used the rejection method in ABC with a tolerance of 0.05 as the rejection method always generates posterior within the prior range. We obtained the posterior range by taking the minimum and the maximum values from the ABC output. This range was then used as a prior range for the next iteration. This cycle is repeated until decrease for all parameters is more than 0.95, suggesting it has reached convergence.

We used SFS as input (x) for the NN and the model category as output (y) and removed the parameters values because they are not needed for this step. We used MinMax scaler from sklearn^59 only on the SFS data as above, and the names of the models are converted to one-hot encoding by pandas.Categorical (from pandas package) and Keras.utils.to_categorical (from Keras package). After concatenating files coming from all the competing models, we shuffled the rows by a custom code.^60 We left out around 1,000 random rows per model to test the power of NN (as a testing dataset) and for ABC analysis and used the rest to train the NN (as a training dataset). The rest of the approach is as described above (see parameter estimation with DL). We also tested these models with a much higher number of simulations (50,000 for training and 10,000 for testing and ABC analysis), but because we did not find any substantial differences in the results, we used 2,000 simulations (1,000 for training and 1,000 for testing and ABC analysis) per model throughout this study.

```
decrease = \frac{Posterior_{max} - Posterior_{min}}{Prior_{max} - Prior_{min}}
```

If the decrease is more than 95% for a parameter, the new posterior estimation is rejected for that parameter. Instead, we take the prior range of this step, expand it by 1% of its width and use it as a prior again. We used this strategy to prevent the posterior from shrinking or collapsing unless NN has found some accurate prediction for the parameter (decrease < 95%) and reduces the probability of missing the correct parameter value due to stochastic effect in a single cycle.

```
Posterior_{min} = Prior_{min} - \frac{(Prior_{max} - Prior_{min}) \times 1\%}{2}
Posterior_{max} = Prior_{max} + \frac{(Prior_{max} - Prior_{min}) \times 1\%}{2}
```