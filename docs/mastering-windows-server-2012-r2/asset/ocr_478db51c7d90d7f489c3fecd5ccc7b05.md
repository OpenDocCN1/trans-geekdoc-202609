Finally, you need to consider how your users connect to the share to use these applications before you limit them based on concurrency. If your users all connect to the share upon logging in (as with a mapped drive) but do not disconnect until logging off, your concurrency limit may be used up on who shows up for work first, and you'll have 100 people using your concurrency limit even if only a small percentage of them are actually using the application. If connections are made only when actually using the application, the user limit will work quite nicely.

# WATCH THE SPACES WITH SC

The sc config command is used to change the configuration of a service. By default the Virtual Service Device (VDS) is not started, so you will use this command to automatically start the VDS on server. For more information about the sc command's options and features, open up a command-line interface and type **sc config**. The server config (sc) command is very particular about spaces. The following command has a space after the == symbol and will work:

```
sc vds start=auto
```

On the other hand, this command will fail since the space is missing:

```
sc vds start=auto
```

+   4. Create a firewall exception for the Remote Volume Management group with the following command. Even though this spans two lines in the book, the entire command should be entered on a single line. spans two lines in the book, the entire command should be entered on a single line.

```
netsh firewall set rule-CA
group="Remote Volume Management" new enable=yes
```

When the command is correct, the output indicates that it has "Updated 3 rules.",

Once the remote computer is configured, you can launch Server Manager on your local computer, select Manage, and select Add Servers. There are three ways to find and add new machines to your local Server Manager. You can add a server by searching through your Active Directory and selecting a joined computer, you can also add a server using the DNS tab by typing in the computer name or IP address, and lastly the Import tab will let you directly call out the network path to the machine or browse network locations to find the needed resource. Using one of these methods, the machine you wish to manage and find click OK. After a moment, Server Manager will be connected to the remote computer. You can now view and manage the remote computer on the All Servers tab in Server Manager. Simply right-click the newly connected remote computer, and a list of management functions will be displayed for you to use, as shown in Figure 13.13.