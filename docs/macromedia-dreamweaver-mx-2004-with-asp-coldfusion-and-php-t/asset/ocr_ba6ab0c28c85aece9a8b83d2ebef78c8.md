The second code block in ASP, which you'll add to momentarily, instantiates the Message object.

```
1 <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-t
2
3 <%
4
5   theSchema="http://schemas.microsoft.com/cdo/configuration/"
6   Set cdoConfig=server.CreateObject("CDO.Configuration")
7   cdoConfig.Fields.Item(theSchema & "sendusing")=2
8   cdoConfig.Fields.Item(theSchema & "smtpserver")="mail.insightbb.com"
9   cdoConfig.Fields.Update
10
11   set cdoMessage=server.CreateObject("CDO.Message")
12   cdoMessage.Configuration=cdoConfig
13
14
15   <html xmlns="http://www.w3.org/1999/xhtml">
16   <head>
```

# 5) Customize the instance so that it can send desired information to the proper email address. To do so, add the following code just above the closing %> (ASP) or  (ColdFusion). PHP users: enter the line of PHP below, in the empty space you created in step 3 above.

For ASP, enter the following code, substituting yourname@yourserver.com with your actual email address:

```
cdoMessage.From="yourname@yourserver.com"
cdoMessage.To="yourname@yourserver.com"
cdoMessage.Subject="This is the message subject"
cdoMessage.TextBody="This is the message body"
cdoMessage.Send
```

Then, ASP users should add two new lines, as follows:

```
Set cdoMessage=Nothing
Set cdoConfig=Nothing
```

For ColdFusion, amend the  tag so that it reads as follows, substituting [enter your email address] with your actual email address:

```
<cfmail from="yourname@yourserver.com" to="yourname@yourserver.com"
=subject="This is the Message Subject">
```

ColdFusion users should then add a new line between the opening and closing  tags and type:

```
This is the message body.
```