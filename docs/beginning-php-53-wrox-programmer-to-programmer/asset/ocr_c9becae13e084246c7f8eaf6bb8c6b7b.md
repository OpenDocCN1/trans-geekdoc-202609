# Chapter 15: Making Your Job Easier with PEAR

```
echo ". Your operating system is " $detect->getOSString() ".</p>";
?>

<body>
</html>
```

Run the script by visiting its URL in your Web browser. You should see a similar result to Figure 15-1.

![](bbox=[0.266, 0.215, 0.833, 0.492])

# How It Works

This simple script kicks off with the standard XHTMLpage header, then includes the Net_UserAgent_Detect package:

```
require_once( "Net/UserAgent/Detect.php" );
```

It creates a new UserAgent_Detect object:

```
$detect = new UserAgent_Detect();
```

The Net_UserAgent_Detect class contains a number of different methods for extracting browser information. In this script, the getBrowserString() method is called to retrieve the visitor's browser name and version as a text string, and getOSString() is called to return the visitor's operating system as a string. These strings are displayed in the page:

```
echo "<p>You are running " $detect->getBrowserString();
echo ". Your operating system is " $detect->getOSString() "."</p>";
```