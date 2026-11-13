The "exit" message is called by a client that wants to exit chat. If the user simply closes the Flash movie, the socket server removes the user from the list on the next loop pass. This gives the user a way to cleanly leave the system and see a "Goodbye" message as he or she is exiting.

```
else if(substr($specialString, 0, 4) == "exit")
{
    $this->serverMessage("Closing Connection: " . $socket);
    $this->notifyClient($socket, "Goodbye");
    $this->endSocket($socket);
}
```

A more advanced chat application would probably have documentation on the Web site. This "help" command shows you another way to deliver the more commonly used commands directly to your connected clients. You will notice this command is very similar to the "man" command that is found in UNIX terminals.

```
else if(substr($specialString, 0, 4) == "help")
{
    $this->notifyClient($socket, "Chat Help:\n"
        . "Type exit to leave chat");
}
```

If no special message is found, then simply broadcast the unedited message to all of the other clients. This system will even display your comment back to you. A more complete application would need to be set up to exclude the author of the comment from being updated.

```
else
{
    $this->notifyClients($allclients, $socket, $buffer);
}
```

As you can see, the initLoop method has a lot of responsibilities and handles a good portion of the entire socket server.

# Master client connection

The createMasterClient method is called when the socket server starts. This method initializes the socket server and creates the master connection to which all other clients connect.

```
private function createMasterClient()
{
    if(($this->masterClient = socket_create(AF_INET, SOCK_STREAM,
        SOL_TCP)) < 0)
    {
        $this->handleError(ChatServer::SOCKET_CREATE_FAIL,
            $this->masterClient);
    }
}
```