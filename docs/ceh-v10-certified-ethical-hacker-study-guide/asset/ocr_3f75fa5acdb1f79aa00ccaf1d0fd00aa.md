ports, the scripting engine is used to perform deeper interactions with the application. The scripts can also make programmatic determinations based on the responses that are pro- vided by the service. The scripting engine modules not only provide functionality to inter- act with the services, including registering ports with nmap so the script is called when the identified port is found to be open, but there are also modules for output that is presented back by nmap when the script is complete.

# Zenmap

You can use the command line to do all your nmap scans, but you don’t have to if you prefer to use a GUI. For years, you had to use the command line because that’s all there was available. There were attempts to create GUIs to overlay on top of nmap, and then one year, under Google’s Summer of Code project, a GUI called Zenmap was created and it has remained the GUI version of nmap for years. It is, as suggested, an overlay for nmap. This means that what you do in Zenmap runs nmap underneath and then the results from nmap are available in the GUI. With Zenmap, you don’t have to think so much about the type of scan you are performing in the sense of the list of scan types I mentioned earlier. Instead, as you can see in Figure 5.3, you select from a scan by name in a pulldown.

# FIGURE 5.3 Zenmap scan types

![](bbox=[0.156, 0.464, 0.856, 0.892])