The first thing you might notice is that the SMTP service installs in a manual startup. To configure the startup parameters, you should configure the service itself using the Services console from the Administrative Tools group (see Figure 19.20).

# FIGURE 19.19n Internet Information Services (IIS) 6.0 Manager console

![](bbox=[0.297, 0.196, 0.881, 0.497])

# FIGURE 19.20 Simple Mail Transfer Protocol (SMTP) service properties

![](bbox=[0.297, 0.532, 0.881, 0.633])

If you install more than the IIS 8 roles, the SMTP service behavior differs upon installation. Specifically, if you install all IIS 6 Web Server roles, then SMTP services will start immediately upon adding the SMTP feature, even though the service configuration has a startup setting of Manual. And although this might be helpful, the first time the server gets rebooted, you'll be wondering why your SMTP services did not restart on their own as well. So, changing the startup setting of the service from Manual to Automatic.

# Adding the SMTP Server Feature

In addition to IIS 8 roles of IIS 6 Metabase Compatibility and the IIS 6.0 Manager console, the SMTP feature also requires the SMTP Server Tools feature. Server Manager utilities, both GUI and CLI, are enough to install these dependencies over SMTP installation. The SMTP Server Tools feature provides the snap-in to the IIS 6.0 Manager console needed to administer SMTP services. To install this required SMTP Server Tools