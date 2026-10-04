# 284 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondonon

```
System.out.println("Number of documents in database is: " +
numberOftems);
// Following record must have (last key + 1) as its key
idx = (int) numberOftems + 1;
System.out.println("Setting index of new record to: " + idx);
// Enabling the toggle/switch to be clicked
cloudSwitch.setClickable(true);
catch (Exception e) {
    System.out.println("Problem fetching number of items: " + e.toString());
}
```

# 4.3.6. Traffic Monitoring in the onCreate() Method

The onCreate() method is created automatically upon building the Android project in Android Studio and is dedicated to processes that take place during the initialisation of the MainActivity.java class, i.e., when the latter is started. It contains the following necessary functionalities.

+   * Mapping the components on the layout to their respective variables.
* Specifying the settings for the line graph.
* Setting the options for the axis configurations and legend.
* Configuring the spinner to hold several choices and actively listen for changes.
* Find the first set of values for the parameters to be monitored.
* Calling the "Monitor," "Stop" and "Go to Analysis" buttons.

The codes found in this section belong to the onCreate() method and related to button calls defined by Listings 4.16 to 4.21.

> Listing 4.16. Overview of onCreate() method in Monitor_App

```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    // Listings 4.17 to 4.21 are included here
}
```