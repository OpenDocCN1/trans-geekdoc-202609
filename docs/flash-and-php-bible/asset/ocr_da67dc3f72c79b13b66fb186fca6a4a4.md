You could call the serverMessage method directly, but using this relay system allows you to
trap errors and keep your code clean. It wouldn’t make sense to have the SHOW_ERRORS condition
in the serverMessage because a message isn’t always an error.

# Ending a connection

The connection ends if the client closes the browser or application. However, the user can also
close the connection by sending the special "exit" parameter. A socket termination method is
used to ensure the array of active connections is properly handled. This method will also remove
the master if no active clients exist, ultimately ending the socket server connection itself.

The array_search function is used to find the socket id to close. This function returns the id
from the array. This is used to remove the connection from the list and terminate the specific
socket connection.

```
private function endSocket($sockID=null)
{
    // close master if no socket is defined
    if($sockID == null)
    {
        $sockID = $this->masterClient;
    }

    $index = array_search($sockID, $this->clients);
    unset($this->clients[$index]);
    socket_close($sockID);
}
```

# Server monitoring

The last method of the chat class is used to print messages about the socket server directly to the
active prompt, generally running on the Web server to which the clients are connecting.

```
private function serverMessage($str)
{
    print $str . $this->LINE_ENDING;
}
```

# Connecting to the socket server

The connection to the chat class built in the previous section is handled by the second PHP file.
This file will be the one you would call when you want to start the chat server. Building the system
in this manner allows you to leave the chat class on its own and duplicate the connection without
modifying the code.