To perform a regression analysis using the Excel Solver, first calculate the sum of the error squares of the difference between the predictions by the regression and the simulation results on a sheet and designate the result as the target cell. Next, the regression coefficients can be calculated by specifying each coefficient of the regression analysis in the variable cells and running Solver to minimize the objective cell. You can check to see if this calculation is correct by creating the same model in the Excel Analysis ToolPak and checking the results.

To create an NN model using the Excel Solver, an activation function that performs a nonlinear transformation is applied to the output of the regression analysis, which is used as a new output. This creates an NN model for one layer. Figure 5.5 shows the NN model and its regression analysis results created using Excel Solver. The explanatory variables are varied on a regular grid, and their objective function values are visualized three dimensionally.

Using the ExNN described in Chapter 2, Section 7, Paragraph 3, a deep learning model can be constructed by specifying the number of layers required and the number of neurons per layer. In this case, the target cell is called the loss function in the NN model. The advantage of the NN model is that it satisfies the universal approximation theory from a

![](bbox=[0.14, 0.58, 0.86, 0.93])

Figure 5.5. The NN model created with Excel Solver and the results of the regression analysis.