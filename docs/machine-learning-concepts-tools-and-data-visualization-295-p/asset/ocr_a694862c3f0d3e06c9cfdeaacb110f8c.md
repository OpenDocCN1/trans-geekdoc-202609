# Create Prediction Model using Microsoft Machine Learning Studio 103

![](bbox=[0.167, 0.083, 0.832, 0.545])

Figure 6-44 Arrangement for prediction model

Place the Score Model, as shown in Figure 6-44, connect the Train Model Block and the Split Block, and click the Run button to train. Let's check the types of irises predicted through visualization and the types of irises stored in the test data.

As shown in Figure 6-45, you can see that 30% of the test data has been applied to the prediction model.

To see the evaluation of the prediction results, add an “Evaluate Model” block to the canvas, and associate it with the “Train Model” block, as shown in Figure 6-46. Then press the “Run” button to run it. When it is done, check the results of the model evaluation with “Visualize”.