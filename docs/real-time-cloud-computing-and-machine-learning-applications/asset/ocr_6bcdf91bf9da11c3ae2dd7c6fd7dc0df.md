# Server and Servlet Architectures for a Cloud-Based Real-Time .

```
out.flush();
out.close();
if (Math.round(classificationMLP) == 2) {
// Sending the values through the socket connection
out.println("Client activity with MLP: browsing");
out.flush();
out.close();
}
if (Math.round(classificationMLP) == 3) {
// Sending the values through the socket connection
out.println("Client activity with MLP: streaming");
out.flush();
out.close();
}
breakbreak;
// Android - LTE Classification analytics
case 5: 
// Fetching the parameters for classification from Android device\mdspeed = readings.getDouble("mspeed");
mspeed = readings.getDouble("mspeed");
prec = readings.getDouble("prec");
psent = readings.getDouble("psent");
// Setting boolean for Android classification to true
fetchClassificationLTE = true;
// Fetching Android LTE values
fetchClassificationValuesLTE();
// Setting the values in a double [] array
values = new double[]{mdspeed, mspeed, prec, psent};
KNNClassificationLTE(this); // Performing KNN Classification
// Printing the numerical label with the highest number of votes and
converting the label to a String object to be printed
System.out.println("The set values belongs to category: " + greatestClass.doubleValue());
if (greatestClass.doubleValue() == 1.0) {
// Sending the values through the socket connection
out.println("Client activity with KNN: idle");
out.flush();
out.close();
}
if (greatestClass.doubleValue() == 2.0) {
// Sending the values through the socket connection
out.println("Client activity with KNN: browsing");
out.flush();
out.close();
n
```