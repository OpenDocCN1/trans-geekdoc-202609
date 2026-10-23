![](bbox=[0.125, 0.145, 0.875, 0.475])

We can see that the JSON here currently contains two top-level items: "`cmdline`" and "`memstats`". Let’s quickly talk through what these represent.

The "`cmdline`" item contains an array of the command-line arguments used to run the application, beginning with the program name. This is essentially a JSON representation of the `os.Args` variable, and it’s useful if you want to see exactly what non-default settings were used when starting the application.

The "`memstats`" item contains a ‘moment-in-time’ snapshot of memory usage, as returned by the `runtime.MemStats()` function. Documentation and descriptions for all of the values can be found here, but the most important ones are: