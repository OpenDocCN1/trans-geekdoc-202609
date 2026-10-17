![](bbox=[0.143, 0.087, 0.857, 0.471])

**FIGURE 5.10** Unable to connect to the service. This indicates that the web page is not up.

After attempting to manually browse to the web application, it appears as though we cannot establish a connection to the website at all. This indicates that the web service is either not running or something is blocking us from reaching it. Let’s jump over to the target on a VM and check what’s going on.

When running the command **systemctl status apache2** we are given information that states that the Apache service is not running. This is likely the reason why the webpage is not responding – let’s start the service with **systemctl start apache2**.

![](bbox=[0.107, 0.688, 0.893, 0.888])

**FIGURE 5.11** Investigating the Apache service on the target system. The service is inactive, this is likely why we are not successful.