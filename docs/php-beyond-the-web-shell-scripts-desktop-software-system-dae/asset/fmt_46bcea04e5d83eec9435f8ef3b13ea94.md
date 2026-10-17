
*   `queue` : This is the `$queue` resource identifier

*   `msgtype` : This is an arbitrary integer which specifies the “type” of message. You can choose to assign your messages an integer corresponding to any kind of criteria you want, and then when receiving messages you can filter by this type field. For instance, you can choose to receive the next message of type “3”, or the next message of any type. This can be useful, for instance, to assign a priority to messages using the type parameter and use that to deal with them in order of priority at the receiving end.

*   `message` : This is the actual message to send. This should be a string, UNLESS you have the next parameter (`serialize`) set to true, in which case you can pass a variable or object of any type which PHP can serialize into a string. In our example for instance we pass a PHP array directly to the `msg_send()` function without calling any kind of encoding function on it first (e.g. `json_encode()` or `serialize()`) because we have the next parameter set to true.

*   `serialize` : If this is set to true, this will automatically call the session module serialization mechanism to serialize the message into a string. This is usually the `serialize()` function (unless you have chosen to use the WDDX serializer or similar). If you are planning to pass data to non-PHP programs using the message queue, you should not use this automatic serialization (which is unique to PHP) and instead use another encoder like `json_encode()` or format your data as XML for instance, depending on which formats the programs you are communicating with will accept.

*   `blocking` : If the queue is full and you try and send a message, the `msg_send()` function will “block”. This means it will sit and wait for space to become available in the queue and hold up your script until that happens. If you set this parameter to `false`, instead of blocking the function will return `false`, set the `errorcode` parameter to `MSG_EAGAIN` (to indicate you should try again later) and let the script continue to run. In this case, it is your responsibility to remember the message and try to send the message again as the `msg_send()` function will forget all about it.

*   `errorcode` : This parameter stores any error code generated in case of an error. If an error occurs, the function will return `false` as well as setting this code.

So in our example above, we use `msg_send()` in blocking mode to send the PHP array `$phpArray` as our message, assigning it as a type “3” message (which is purely arbitrary in our case), using automatic serialization of the array into a string and catching any error codes in `$errorCode`.

Now we look at our `display2.php` script. After calling `msg_get_queue()` to join the queue, we start a continuous loop (using `while(1)`) which will try and read a message from the queue each time we go through the loop. We’ve added a `sleep(1)` one second delay to space out our message requests and show that the timing of our message requests isn’t important (you can change this to another value and it will work just as well, or indeed remove it completely and grab all the messages without delay). To get a message, we use `msg_receive()`, which takes the following parameters:

*   `queue`: The `$queue` resource identifier

*   `desiredmsgtype`: The type of message you want to receive. If this is 0, you will simply get the next message in the queue. If it is set to a positive integer, say 5, you will get the next message that was sent using 5 as the type parameter in `msg_send()`. If it is a negative integer, say -3, you will get the next message on the queue with the lowest type that is less than or equal to the absolute (non-negative) value of this parameter. e.g if we specify -3 we will get the first message with type 1, 2 or 3 (and if there are multiple messages with these types, then we take the first message that has type 1, then when all the 1’s are gone the first with type 2 and so on.).

*   `msgtype`: This is the actual type of the message that we have received. This is useful when we specify a negative value for `desiredmsgtype` above to get a message from a range of types, and want to see what type the message we were given actually is.

*   `maxsize`: This specifies the maximum size (in bytes) of the message that you are willing to receive. If the message that you would receive is bigger than this size then the `msg_receive()` function will either return false and not return a message at all, or if `MSG_NOERROR` is set in the `flags` parameter below, it will instead truncate the message and return just the first `maxsize` bytes. Be aware that the `msg_receive()` function allocates a block of memory equal to `maxsize` before it tries to read the message. This means that even if the message is small (e.g. 10kb), if you specify too large a size here (e.g. 1Gb when you only have 512Mb memory free) your script will crash.

*   `message`: This is the actual message you receive. If the `unserialize` parameter below is set to `true`, any PHP types like arrays or objects will be unserialized and returned as the correct type. If `false`, you will receive the message as a (potentially serialized) string.

*   `unserialize`: If true, the contents of message will be automatically unserialized.

*   `flags`: You can specify the following flags: 

    *   `MSG_IPC_NOWAIT` : If there are no suitable messages to receive, by default `msg_receive()` will “block” the execution of the script and sit and wait for a new message to arrive. If you set this flag, the the script will not block, will return the integer value for `MSG_ENOMSG`, and your script will continue.

    *   `MSG_EXCEPT` : If you ask for a message of a particular type using a positive integer in `desiredmsgtype` above, and you set this flag, you will get a message of ANY type EXCEPT the one you have specified.

    *   `MSG_NOERROR` : Stops errors when the message is too big, see `msgtype` above for details.

*   `errorcode`: If an error occurs, the `msg_receive()` function returns `false` and this parameter is set to the `relevant` error code.

So in our example, we ask for a message of maximum 1024 bytes where the type is -4 (that is to say, its type is 1, 2, 3 or 4). Our `generator2.php` script creates messages of type 3 and all are less than 1024, so they will all match and be returned. `$realType` will be set to 3, and `$phpArray` will contain our data as an array because we have set `unserialize` to true. We haven’t set the `MSG_IPC_NOWAIT` flag, so if there are no messages our script will “block” at the `msg_receive()` command waiting for new messages.

You can use `msg_queue_exists()` to check that a message queue exists before trying to use it, and `msg_remove_queue()` to destroy a queue when you are done with it. To get more information about a queue, you can call `msg_stat_queue()`, which returns an array with the following keys:

*   `msg_perm.uid` : The uid (User ID) of the process that owns (created) the queue.

*   `msg_perm.gid` : The gid (Group ID) of the process that owns (created) the queue`.

*   `msg_perm.mode`: The file access mode (permissions) of the queue.

*   `msg_stime` : The time that the last message was added to the queue.

*   `msg_rtime` : The time that the last message was removed from the queue.

*   `msg_ctime` : The time that the queue was last changed (either a message was added or removed).

*   `msg_qnum` : The number of messages currently in the queue.

*   `msg_qbytes` : The maximum size in total of the message queue, in bytes.

*   `msg_lspid` : The pid (Process ID) of the process that last added a message to the queue.

*   `msg_lrpid`: The pid (Process ID) of the process that last removed a message from the queue.
