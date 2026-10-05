# An Efficient Platform for the Automatic Extraction of Patterns in ... 303

![](bbox=[0.235, 0.096, 0.765, 0.252])

**Figure 9: Execution time for an increasing number of functions.

Figure 10 presents another view of the same data. That figure displays the execution time performance per function, increasing the number of functions in the program. For small programs, there is an initialization penalty causing a higher execution time to process a number of functions. When the program size grows, this initialization cost becomes negligible. From 5,000 functions on, the execution time per function converges (the standard deviation is lower than 3.4%), showing that the performance of the platform is not decreased for big input programs.

![](bbox=[0.173, 0.506, 0.794, 0.672])

**Figure 10: Execution time per function, increasing the number of functions.

# Increasing Max Offset and Max Size

We modify the values of the Max Offset and Max Size parameters used to obtain the binary subpatterns. We use 4 modules, each implemented with 750. Max Offset is incremented from 0 to 8, fixing Max Size in 4. We apply the same method to analyze the influence of Max Size in runtime performance, increasing its value from 1 to 8 and fixing Max Offset to 4.

Figure 11 shows both variables. We can see how Max Offset has a linear influence on execution time. The regression line shown in Figure 11 has a