Super-views have the following chars:
- a super-view cannot be directly configured by commands. It groups together the configuration of the set of views that constitute it;
- a view can be shared between several super-views;
- users connected to a super-view can access all commands configured in the views that are part of the super-view;
- deleting a super-view does not delete all views associated with this view.

To configure a view, proceed as follows:

| Command | Description |
|---|---|
| Router(config)# parser view Super-view-name Superview | Creates a super-view in global configuration mode. |
| Router(config-view)# secret password | Assigns a password to the super-view. |
| Router(config-view)# view view-name | Assigns an existing view to the super-view. |
| Router# username U1 view Super-view-name | Assigns a super-view to a user. |
| Router# enable view view-name | Connects to the super-view. |
| R1#show parser view all | Displays the list of super-views. |

# 2.6.6. Securing configuration files and the IOS system

The Cisco IOS system provides the ability to create copies of the IOS image or
of the configuration file. The archives are stored in “bootset” format, which is
protected against deletion.

To archive the IOS image file or the configuration file, proceed as follows:

| Command | Description |
|---|---|
| R1(config)# secure boot-image | Secures the IOS image by hiding it in Flash
memory. This can only be seen in ROMMON mode. |
| R1(config)# secure boot-config | Secures the configuration file. |
| R1# show secure bootset | Displays the archive status of the Cisco IOS image
and the configuration file. |