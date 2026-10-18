```
<head>
<title>Chatroom Script</title>
<meta http-equiv="Content-Type" content="text/html; charset = ISO-8859-1" />

<script type="text/javascript" src="getxmlhttprequest.js">
</script>
<script type="text/javascript" src="example18-5.js">
</script>
<style type="text/css">
#chatroom {
    float: left;
    width: 300px;
}

#messageform {
    float: left;
    width: 250px;
}
</style>
</head>
<body onload="startJS(1);">

<!-- File: example18-5.htm -->

<h2>Chatroom:</h2>

<div id="chatroom">
</div>
<div id="messageform">
<form action="" method="post">
<p>UserId: <input type="text" name="strUserId" id="strUserId" /></p>
<p>Message: <input type="text" name="strMessage" id="strMessage" /></p>
<p><input type="button" value="Send Message" onclick="startJS(2);" /></p>
</form>
</div>
</body>
</html>
```

Firstly, the 'getxmlhttprequest.js' and 'example18-5.js' JavaScript files are loaded:

```
<script type="text/javascript" src="getxmlhttprequest.js">
</script>
<script type="text/javascript" src="example18-5.js">
</script>
```

An embedded CSS-style definition is included to define the styles of the message form, where the user enters new messages, and the chatroom, where the messages are displayed:

```
<style type="text/css">
#chatroom {
```