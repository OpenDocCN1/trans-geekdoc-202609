Now that the new Orange site has been created, you can employ either of the two IIS Manager’s navigation methods you learned earlier to test the new site by browsing to it (as shown in Figure 19.15). Remember to disengage the IE Enhanced Security Configuration setting or add the http:///orange URL to your list of trusted sites if necessary.

Figure 19.15
Orange website

![](bbox=[0.313, 0.213, 0.753, 0.553])

# CREATING A SITE VIA POWERShell

Alternatively, you can use PowerShell to create a site on your web server. The beauty of PowerShell is that you can use scripts for later use. The scripts could even be parameterized to allow the insertion of the site name and other values at runtime. Scripted creation helps you deploy a site-like structure and content across a network load-balanced server farm as disaster recovery and deployment for change control.

The New-WebSite cmdlet is the tool for PowerShell site creation. Here’s the PowerShell syntax that would create a site called Oranges on TCP port 80 pointing to the assumed directory path ending in \inetpub\oranges and using a custom host header of oranges:

```
New-WebSite -Name Oranges -Port 80 -HostHeader Oranges -PhysicalPath "$env:systemdrive\inetpub\oranges"
```

When creating a site with PowerShell, if you omit the -Id parameter (as shown here), it causes IIS to simply assign the next-available ID number to the new site. Also, if you had failed to provide the -PhysicalPath parameter, then no applications or virtual directory would have been created for the new site, and you would have to manually add those settings to the new site once it was created.