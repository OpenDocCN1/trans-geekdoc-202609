```
default:
    PEAR::raiseError('Unhandled error: ' . $event);
}
}
?>
```

+   - Declare a constructor that calls the parent constructor and performs any needed custom logic.
- Declare the update method with the signature shown. $subject is the request or client instance to which the listener is attached. $event is a string containing one of the events shown in the switch statement.
- $data is data specific to events related to reception of the server response.
- Request and response events occur within HTTP_Request instances. Client events occur within HTTP_Client instances.
- Note that not all events need to be handled, only those with which you are concerned.

The attach method in HTTP_Request takes a single parameter, a listener instance. The equivalent method in HTTP_Client takes two parameters, a required listener instance and an optional boolean flag. When the latter is false (which it is by default), attached listeners will not be propagated to requests created within the client instance. That is, a listener added will not be notified of request and response events, only client events. To have an added listener receive all events, explicitly specify the $propagate parameter to be true when calling attach.

# Wrap-Up

For more information on the PEAR packages covered here, see these resources listed below.

+   - http://pear.php.net/manual/en/package.http.http-request.php