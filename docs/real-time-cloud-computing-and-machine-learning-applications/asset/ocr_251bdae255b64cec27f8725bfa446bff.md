```
out.close();
break;
// PC - Regression analytics
case 8:
// Fetching the parameters for regression from PC device
predictionTime = readings.getInt("predictionTime");
windowSize = readings.getInt("windowSize");
// Set the fetching for PC regression values to true
fetchRegressionPC = true;
// Fetching regression values for PC
fetchRegressionValuesPC();
localhostRegression = true;
MLPRegression(); // Performing MLP Regression
System.out.println("Sending flow through socket: " + mlrPrediction + "\n" + mlPrediction());
// Sending the values through the socket connection
out.println("Packets received with MLR: " + Math.round(mlrPrediction) + "\n" + \
```