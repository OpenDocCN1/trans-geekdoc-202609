```
XAxis x = chart.getXAxis();
x.setTextColor(Color.BLACK);
x.setDrawGridLines(true);
x.setAvoidFirstLastClipping(true);
x.setEnabled(true);
```

```
// Setting options for the Y-axis and enabling the left part
YAxis yL = chart.getXAxisLeft();
yL.setTextColor(Color.BLACK);
yL.setDrawGridLines(true);
// Disabling the axis which would appear on the right
YAxis yR = chart.getXAxisRight();
ynR.setEnabled(false);
```

# 4.3.9.2. Creating and Populating the Spinner

+   1. The Spinner object, used to select the parameter displayed on the live monitor as described by the switch-case statement in Listing 4.29, is paired with an ArrayAdapter object of type own. The ArrayAdapter object is responsible for populating the spinner with a list of choices. These two variables have previously been defined as global variables in the MainActivity.java class.

+   2. After allocating the spinner a particular spot on the layout and creating its object in the Java class, it needs to be populated with the different network statistics that the user will select from. This can be created in an XML file in which this case is referred to as a string resource file whereby a String array is used to list all the parameters. Usually, in Android application development, such files are stored in the "values" folder. A new "Values Resource File" can be found in the Android pane. By right-clicking on the values folder and selecting the option as shown in Figure 4.19.

![](bbox=[0.108, 0.651, 0.893, 0.856])

Figure 4.19. Creating a value resource file.

The name of the XML file is entered, which in this case is "strings" and the file is created as shown in Figure 4.20.