# FIGURE 13.4 Functions in loops

![](bbox=[0.2, 0.09, 0.9, 0.67])

# Some nice holiday temperatures:

+   25°C = 77°F
+   26°C = 78.8°F
+   27°C = 80.6°F
+   28°C = 82.4°F
+   29°C = 84.2°F
+   30°C = 86°F
+   31°C = 87.8°F
+   32°C = 89.6°F
+   33°C = 91.4°F
+   34°C = 93.2°F
+   35°C = 95°F
+   36°C = 96.8°F
+   37°C = 98.6°F
+   38°C = 100.4°F
+   39°C = 102.2°F

Also, note that the function invocation no longer specifies the temperature type:

```
temperatureConvert($intCount);
```

The output for the above script is the same as that shown in Figure 13.4. In some of our examples of user-defined functions, we have shown that we can pass values to the function and these can be used to affect the functionality of the function itself. What we have not yet seen is how we can return a value from a function.

# Returning a value

The keyword ‘return’ is used to return a value from a function:

```
return value;
```