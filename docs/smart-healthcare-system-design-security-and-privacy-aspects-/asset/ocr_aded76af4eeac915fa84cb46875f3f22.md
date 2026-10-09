the monitoring server. The Python script ran for 25 min on the monitoring server to plot figures in real-time.

Figures 10.14 to 10.19 show the graphic display of the data received from the six sensors.

Each figure presents the data from a particular sensor, and each has three panels. In each case, the uppermost panel, labeled (a), presents the actual data gathered by the sensor. Because the sensors were deployed in different locations in the test section, each sensor measured a slightly different pressure than the other sensors. The middle panel, labeled (b), presents the data published, transmitted from the RasPi to the monitoring server based on EEDF policy. The EEDF protocol eliminated the continuous reading of similar data and drops these data before published it to the MQTT broker. The bottom panel, labeled (c), shows typical data collected from the MQTT broker and retrieved to the original data collected, based on the PNDD algorithm.

To assess how accurately, reliably and economically the PNDD algorithm reproduced the original date we compare, for each sensor, panels (a) and (c) in Figures 10.14 to 10.19.

![](bbox=[0.18, 0.49, 0.81, 0.87])

**Figure 10.14** Data from sensor 1.