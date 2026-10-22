+   - Original time series is being used
+   - An exhaustive search for the number of hidden nodes [1,20]
+   - For the WANN approach (model1b(1-220)-model4b(1-220)) in total 880 (220x4) models
+   - Perform a-trous wavelet transform to the original time series
+   - An exhaustive search for the number of hidden nodes [1,20] and number of decompositions [1,11]
+   - Evaluate models performance (model1a-model4a and model1b-model4b)
+   - Error metrics RMSE, Cor, NSE, PERS, and others
+   - Select the best fold for the ANN and the WANN model among the model1, model2, model3, and model4 models
+   - Once the best model is selected, de-noising by threshold is applied to the best WANN model, via optimization
+   - Individual threshold values were found for all the detail coefficients via optimization, the objective function was set to the minimum RMSE

# 9.3.2. Input Variable Selection (IVS)

Forward selection, correlation, and average mutual information were implemented to select the most appropriate variables. The first consists of a linear increment search strategy in which variables are incremented one at a time until performance does not increase. The method is considered slow because the execution of a model is required. The model-free approach takes some dependency measures (linear and nonlinear between input and target) to find the right variables, attractive in terms of computational efforts because no model needs to be run. Model 2 (equivalent to model 5 suggested by correlation and AMI) described in section 9.3.1 was chosen, since it shows the best performance values. For the pragmatic purposes of the present study, the authors do not elaborate on the detailed development of this process, since the particular conditions of the case analyzed (rapid reaction basin and daily data) generate a reduced space for the selection of variables, and this prevents an objective assessment of the strengths or weaknesses of the IVS methods analyzed. For more details on the methods available for the selection of input variables, it is suggested to refer to May et al. (2011).