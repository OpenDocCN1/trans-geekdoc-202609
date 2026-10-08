# Core PHP Programming

```
fputs($fp, "QUIT\r\n");
fclose($fp);

if(substr($line, 0, 3) != "250")
{
    //mail server doesn't recognize
    //this address, so it must be bad
    $error = $line;
    return(FALSE);
}
else
{
    //address recognized
    return(TRUE);
}
```

$error = "Unable to reach a mail exchanger!";
return(FALSE);

if(verifyEmail("leon@clearink.com", &$error))
{
    print("Verified!<BR\n");
}

else
{
    print("Could not verify!<BR\n");
    print("Error: $error<BR\n");
}

SMTP servers precede each message with a numerical code, such as the 250 code mentioned above. When first connecting with a server, any number of 220 messages are sent. These contain comments, as the AOL servers' remainders not to use them for spam. Special code marks the end of the comments; the server simply stops sending. Recall by default the fgets function returns after encountering the maximum number of characters specified or an end-of-line marker. This script will not work in the case of an indeterminate number of lines. The script will wait forever after the last comment. Socket blocking must be turned off to handle this issue.

When set_socket_blocking off, fgets returns immediately with whatever data is in the buffer. The strategy is to loop continuously, checking the buffer each time through the loop. There will likely be some lag time between establishing a connection and receiving the first message from the server. As as 220 messages appear, the script must begin watching for the data to stop flowing, which means the server is likely waiting for a command. To avoid the situation where a server