```
ob_end_clean();
// Clean out the main buffer
ob_clean();
// Display an error message
echo '
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Temporary Interruption </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<h2>Temporary Interruption</h2>
The site is currently down for non-scheduled maintenance.<br />
Please try again shortly
</body>
</html>';
// End and flush the main buffer
ob_end_flush();
// Stop execution
exit();
break;
// Handle WARNINGs
case E_USER_WARNING:
// Clean out the main buffer
ob_clean();
// Display an error message
echo '<b>Warning:</b> ' . $errMsg;
break;
// Handle NOTICEs
case E_USER_NOTICE:
// Display an error message
echo '<b>Notice:</b> ' . $errMsg;
break;
}
}
```

This custom error handler is capable of dealing with three error levels, E_USER_ERROR, E_USER_WARNING, and E_USER_NOTICE. You'll notice that the way it handles the output buffer is a little different at each level. An E_USER_ERROR message, which, you'll remember, is a fatal error, results in the handler clearing out both output buffers (there are two, the reason for which will become obvious in a moment), and displaying a message about the site being down; this completely