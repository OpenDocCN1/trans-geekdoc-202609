# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 669

![](bbox=[0.237, 0.093, 0.762, 0.343])

Figure 6.46. JComboBox to Change Current Weather Parameters.

+   4. The weather parameter being observed on the live graph can be changed using the JComboBox as shown in Figure 6.46.
5. As an example, the "Wind Direction" parameter is selected as shown in Figure 6.47.

![](bbox=[0.237, 0.48, 0.762, 0.73])

Figure 6.47. Changing Current Parameter Being Observed.

+   6. The "Stop Monitoring" button is used to stop the monitoring process.

# 6.4.5.2. Downloading Weather Data

+   1. To download data from the local server, the user needs to choose "Local" in the Source JComboBox. The IP address of the local server running is then entered into the "Local Server". To download data from the Cloudant database, the user needs to choose "Cloud" in the Source JComboBox.