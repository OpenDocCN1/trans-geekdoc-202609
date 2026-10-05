# 7.1.2 Examples

In practice, the set of features S usually only contains one feature or a maximum of two, because one feature produces 2D plots and two features produce 3D plots. Everything beyond that is quite tricky. Even 3D on a 2D paper or monitor is already challenging.

Let us return to the regression example, in which we predict the number of bikes that will be rented on a given day. First we fit a machine learning model, then we analyze the partial dependencies. In this case, we have fitted a random forest to predict the number of bicycles and use the partial dependence plot to visualize the relationships the model has learned. The influence of the weather features on the predicted bike counts is visualized in the following figure.

![](bbox=[0.173, 0.355, 0.755, 0.532])

Figure 7.1: PDPs for the bicycle count prediction model and temperature, humidity and wind speed. The hotter, the more bikes are rented. This trend goes up to 20 degrees Celsius, flattens and drops slightly at 30. Marks on the x-axis indicate the data distribution.

For warm but not hot weather, the model predicts on average a high number of rented bicycles. Potential bikers are increasingly inclined in renting a bike when humidity exceeds 60%. Interestingly, the predicted number of bike rentals does not fall when wind speed increases from 25 to 35 km/h, but there is not enough training data, so the machine learning model could not learn a meaningful prediction for this range. Although intuitively, I would expect the number of bicycles to decrease with increasing wind speed, especially when the wind speed is very high.

To illustrate a partial dependence plot with a categorical feature, we examine the effect of the season feature on the predicted bike rentals.

We also compute the partial dependence for cervical cancer classification. This time we fit a random forest to predict whether a woman might get cervical cancer based on risk factors. We compute and visualize the partial dependence of the cancer probability on different features for the random forest: