In the steps that follow, ASP users will write a script in which they can see each of these steps in action. ColdFusion and PHP users will discover that their respective languages hide much of this complexity, though traces of it are still visible.

The following steps are separated to reflect the different stages of using an object.

NOTE These steps continue from the last task, “Writing the Code to Send a Message.”

+   3) Using the code view, position the cursor at the beginning of line 2 (that is, just before the opening <html> tag) and press Enter/Return several times.
+   In this step, you are merely making room for a new script.

+   4) ASP and ColdFusion Users Only: To instantiate and give identity to a new mail object, enter the following code:
+   For ASP:

```
<%
theSchema="http://schemas.microsoft.com/cdo/configuration/"
Set cdoConfig=server.CreateObject("CDO.Configuration")
cdoConfig.Fields.Item(theSchema & "sendusing")= 2
cdoConfig.Fields.Item(theSchema & "smtpserver")="your.SMTP.server.com"
cdoConfig.Fields.Update

set cdoMessage=Server.CreateObject("CDO.Message")
cdoMessage.Configuration=cdoConfig
%>
```

For ColdFusion:

```
<cfmail>
</cfmail>
```

ASP users: be sure to replace the highlighted code “your.SMTP.server.com” with
the name or IP address of your actual SMTP server. This is most likely the same
server as the one listed for outgoing email in your email client, such as Microsoft
Outlook Express.

The ColdFusion code is fairly self-explanatory: These two tags tell ColdFusion to
create a new mail object. It still needs help before it’s useful, but at least you’ve
created it. Behind the scenes, ColdFusion also gives this mail object a unique ID,
so in this simple step you have accomplished several tasks.

The ASP code is (not surprisingly) somewhat more cryptic. In the first code block, you
provide the information ASP needs to actually connect to the mail server. It’s cryptic,
to be sure, but you should be able to use it as-is on any modern Windows server.