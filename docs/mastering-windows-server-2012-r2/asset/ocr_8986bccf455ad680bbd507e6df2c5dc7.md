Add the following component into pass 4, “4 specialize.” You use ComputerName, well, to set the name of the computer. That's not very mysterious. You set it to *. This tells the OS installer to generate a random name. You could type in something there if you wanted. TimeZone to configure the system clock. In this example, we've set it to the USA Eastern Time Zone. A list of available zones is available by passing F1:

| Pass | Component | Property | Value |
|---|---|---|--|
| 4 | AMD64_Microsoft-Windows-Shell-Setup | ComputerName | * |
| | | TimeZone | Eastern Standard Time |

Add the following subcomponent to pass 7, “7 oobeSystem.” Configure the Windows Firewall using NetworkLocation. Setting it to Work configures the firewall to be enabled but loosened suitably for a typical corporate network. ProtectYourPC on automatic updates and config it automatically. This component shows how you can add a little extra to your installation that is not otherwise available in a manual installation:

| Pass | Component | Property | Value |
|---|---|---|--|
| 7 | AMD64_Microsoft-Windows-Shell-Setup\OOBE | HideEULAPage | True |
| | | NetworkLocation | Work |
| | | ProtectYourPC | 1 |

The last component you'll set up is a good to keep in mind for laboratory environments where you might be using MSDN or TechNet licensing. Those subscriptions give you a limited number of activations for every license key. Your typical lab machine has a very short life, so it is pointless to use your valuable activations. This component allows you to disable the default process of autactivation of your installation:

| Pass | Component | Property | Value |
|---|---|---|--|
| 7 | AMD64_Microsoft-Windows-Security-Licensing-SPPUX | SkipAutoActivation | False |

Those are all the components you want to add. Now you're going to validate the answer file. On the Tools menu, select Validate Answer File. This will go through the properties and the values that you have entered. Anything that is glaringly wrong will lead to an error in the Messages pane. Everything should be OK if you've entered the components and property values as illustrated so far (see Figure 2.77).
You can save your answer file now. Click the File menu, and select Save Answer File As. Save it as autounattend.xml in a location of your choice, such as C:\Answer\autounattend.xml (see Figure 2.78).