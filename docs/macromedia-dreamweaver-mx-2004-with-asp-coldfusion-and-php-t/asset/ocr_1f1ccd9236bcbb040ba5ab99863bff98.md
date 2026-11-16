When you close the dialog, Dreamweaver creates a new folder in your site, called Connections, with a new file inside called conn_newland.asp. You should also notice that the Databases panel now has an expandable listing of the database and its assets.

![](bbox=[0.255, 0.135, 0.445, 0.305])

9) Select the Connections folder in the Files panel, and click the Put button to upload it to the server.

You are ready to create a recordset and start binding database data. Skip ahead to the task. “Retrieving Recordsets and Displaying Database Information.”

# COLDFUSION USERS (RUNNING COLDFUSION LOCALLY OR CONNECTING TO A REMOTE SERVER)

This section is for all ColdFusion users, regardless of how they connect to their server.

ColdFusion users who connect to a remote server must have the administrator for that server grant them RDS login information—which consists of a password. Without RDS login, you will not be able to complete this book.

1) Open index.cfm.

It doesn’t matter which page of your site is open when initially creating the connection. Dreamweaver creates the connection for the whole site. You’ve opened index.cfm because you will add dynamic content to that page in the next task.

2) Open the Databases panel, in the Application panel group. Click the Specify the RDS login for your ColdFusion server link, enter your password, and click OK.

RDS login grants developers permission to access the ColdFusion server, which is necessary for defining and using data sources.

![](bbox=[0.255, 0.82, 0.685, 0.905])