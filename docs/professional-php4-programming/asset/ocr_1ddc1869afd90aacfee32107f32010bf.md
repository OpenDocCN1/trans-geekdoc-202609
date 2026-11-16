```
//Attempt to open a file and read a line of text from it
if ($file = @fopen("nosuchfile.txt", "r")) {
    $Text = (fgets($file, 101));
} elseif ($verbose) {
    //if we have turned on verbose error reporting
    myLog("Failed to open nosuchfile.txt");
    echo($php_errormsg);
    //corrective action is to use an alternative line of text
    $Text = $default_text;
} else {
    //error reporting turned off
    myLog("Failed to open nosuchfile.txt");
    $Text = $default_text;
}

echo("Text read: " . $text);

//Simplified version of an error logging function
function myLog($msg)
{
    echo("<h2>" . $msg . "</h2>");
}
?>
```

The script above attempts to open a file and read a line of text from it. In the event that it is unable to do so, it uses an alternative line of text. We have a $verbose flag which helps us determine if the error reporting is to be verbose or succinct. Using the @ operator we are able to suppress the error message when the error occurs and later display the error message based on the value of the $verbose variable.

In the succinct case we simply log the error and take corrective action, which in this case is to assign the $text variable an alternate text value. In the verbose case we log the error and also display the system error message before taking corrective action.

# Error Recovery

When we test the return value of a function and discover an error condition, we now have the ability to display a friendlier error message and bail out or take corrective action. This corrective action can be as simple as performing certain application-specific housekeeping tasks and then gracefully terminating the script or as complex as switching to an alternate algorithm or data source.

```
<?php
//Error_Rec.php
class Connection_Manager
{
    var $connections;

    //This function opens a connection and adds it to a list
    //of open connections
    function openConnection($host, $user, $pass)
    {
        //attempt to connect to a mysql database
```