# BEFORE-AND-AFTER BACKUPS

Like data and other operating system changes, backups should be performed directly before a change is made, as well as after the change is made to ensure that both sides of the GPO are captured.

There will be a time when you want to see the list of GPOs that you have backed up. To see this list, right-click the Group Policy Objects node within the GPMC and select the Manage Backups menu option. This will launch the Manage Backups interface, from here you can restore, delete, and view the settings of a backed-up GPO.

FIGURE 9-30
GPMC allows you to manage the GPOs that you have backed up.

![](bbox=[0.35238095, 0.33333334, 0.8476191, 0.68571428])

Restore The Restore feature will allow you to restore the "archived GPO" over the "production GPO." You can imagine how important this might be!

Delete The Delete option allows you to clean-house the archived GPOs, especially those that are of no use anymore or those that are really old. There's no reason to clog your servers with information you will not need in the future.

View Settings The View Settings option allows you to view the contents of the GPO, as well as all the other key information such as delegation, security, links, and so on. Figure 9.31 illustrates the HTML page that is displayed after selecting the View Settings option.