# Server and Servlet Architectures for a Cloud-Based Real-Time ... 739

# 7.1.14. the predictActionPerformed () Method

When the "predict" button is clicked, the predictActionPerformed() method is invoked. An anonymous thread is created to not block the main thread with the training of the neural network and regression models creation. The window size and prediction time are fetched from the appropriate JTextField. The analytics() method is called to obtain the results of the prediction. The JSONObject is formatted into a more readable form using the formatData() method. The codes for the method are shown in Listing 7.19.

# Listing 7.19. predictActionPerformed () Method

```
private void predictActionPerformed(java.awt.Event event) {
  new Thread(() -> {
    //Window for Regression Model
    int r_window = Integer.parseInt(window_s.getText());
    int pred_t = Integer.parseInt(ptime.getText());
    //Perform Analytics using the analytics() method
    JSONObject analytics = analytics(window, pred);
    //format the result into a readable form
    String formatted = formatData(analytics.toString());
    //displays the result in the text field
    result.setText(formatted);
  }).start();
```

# 7.1.15. Rounding the Output to One Decimal Field

To round the output to one decimal, the roundOutput() method in the MainFrame class is used. This method uses the DecimalFormat class which is a concrete subclass of NumberFormat formats decimal numbers. It has a variety of features designed to make it possible to parse and format numbers in any locale. The code for the method is shown in Listing 7.20.

# Listing 7.20. Round output to 1 decimal

```
/**
 * @param array An array of values that need to be rounded off to 1 dp
 * @return an array [@rounded[]] of rounded values to 1dp
 */
public static float[] roundOutput(float[] array) {
  DecimalFormat df = new DecimalFormat("#.#");
  df.setRoundingMode(RoundingMode.HALF_UP);
```