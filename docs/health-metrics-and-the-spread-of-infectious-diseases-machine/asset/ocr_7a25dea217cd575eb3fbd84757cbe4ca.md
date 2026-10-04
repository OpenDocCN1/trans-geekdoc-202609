# Residuals vs Predicted Values

![](bbox=[0.111, 0.085, 0.863, 0.235])

(a) Residuals vs Predicted Values

(b) Normality Test of the Residulas

Figure 8.5 GBM Model Results on DAYLs due to Rabies; Residuals Distribution and Normality Test

```
geom_line(aes(y = Actual,
              color = "Actual"),
              linetype = 1) +
geom_line(aes(y = Predicted,
              color = "Predicted"),
              linewidth = 1,
              linetype = "dashed") +
labs(title = "Actual as Predicted Values Over Time",
      x = "Time", y = "Value") +
  scale_color_manual(name = 
      values = c("Actual" = "navy",
      "Predicted" = "orange"))
```

In conclusion, the H2O GBM model performed well on the rabies dataset, with a low RMSE and MAE. The residuals were normally distributed, indicating that the model's predictions were accurate. The actual vs predicted plots show a good fit, and the time series plots indicates that the model captured the trend in the data.

```
h2o.shutdown(prompt = FALSE)
```

# 8.3.3 Example: General Infection with Keras

The following example shows how to use the {keras}, a package that facilitates the creation and training of neural networks and deep learning models. They provide a user-friendly interface to build models, whether they are simple neural networks or complex deep learning architectures, particularly useful for handling connection networks. More detailed explanation of how a neural network can be found

In this case the SEIR model (susceptible, exposed, infected and recovered) is used, as seen in Chapter 6 chapter, to simulate the spread of a general infection in a population of 1000 individuals over 160 days. For some types of infections, the latency period is significant as it is the time during which infected individuals are not yet infectious themselves. During this period the individual is in compartment E (for exposed).