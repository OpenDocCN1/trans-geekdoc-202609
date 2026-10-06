+   1. Open your Windows 8 or Server 2012 R2 computer to view the C:\Windows\PolicyDefinitions folder.

+   2. Right-click the PolicyDefinitions folder, and select Copy.

+   3. Open the C:\Sysvol\sysvol\<domainname>Policies folder on any of the domain controllers for your domain.

+   4. Right-click the Policy folder, and select Paste.

The result will be that you now have copied the ADMX/ADML folder structure and files on the domain controller, as seen in Figure 9.25. Since the folder exists in the domain controller, it will automatically be replicated to all the other domain controllers in the domain.

![](bbox=[0.095, 0.333, 0.874, 0.713])

To verify that you are now consuming the ADMX files from the central store, just edit a GPO and view the text under Administrative Templates folder in the GPME.

If you have a custom ADMX/ADML file after creating the central store, you will need to copy the ADMX file to the PolicyDefinitions folder and the ADML file to the en-US folder. The new settings will show up in the GPME!

# ## Restricting Internet Explorer

For every setting in Internet Explorer, there is possible to disable it. Considering a good deal of time is spent surfing the Web, it is a particularly crucial and clever then