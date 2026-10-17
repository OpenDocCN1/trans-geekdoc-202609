
Once we have our data, which should be the `$jsonArray` string padded with spaces, we `trim()` off the spaces and `json_decode()` the string back into an array which we `print_r()` out.

Now we will return to the last two lines of `generator.php`, calling `shmop_delete()` and `shmop_close()`. `shmop_delete()` doesn’t actually delete the memory segment, instead it “marks it for deletion”. This means that no new processes can open the memory segment, but existing processes which have already opened it can continue to access it. It will remain accessible until all of those existing processes close it (or exit), at which point it will be deleted.

You can see this deletion process in action by running these two scripts. `generator.php` will exit after 20 seconds, and `display.php` will keep running forever (due to the `while(1)` loop). Once `generator.php` exits, you will notice that `display.php` keeps outputting the same 3 random numbers each time. This is because although we’ve marked the memory segment for deletion in `generator.php`, `display.php` still has it open and so it can still read it (albeit getting the same value each time as nothing is updating it). If you kill `display.php` and start it again (without starting `generator.php`), you will find that it now reads nothing, as the memory segment was deleted when the previous `display.php` process (the last one using it) exited.

The other peculiarity is that we call `shmop_delete()` before we call `shmop_close()`. The reason is that if we close it first, PHP will not have the internal reference any-more and so won’t know what memory segment to mark for deletion. Once you have called `shmop_delete()`, you can’t do anything else within your script to the memory segment other than closing it. You must have appropriate permissions to be able to mark a segment for deletion. You should ensure that you mark your memory segments for deletion at some point before all of your processes are finished with it. Otherwise you will end up with a “memory leak”, i.e. memory is “allocated” and thus can’t be used by other programs, lowering the amount of available memory to the system as a whole.

Of course the `shmop` functions only deal with transferring the data between processes. Understanding or parsing the data is left as an exercise for the programmer. If the application you are communicating with doesn’t dictate the format (for instance if you are developing the system yourself rather than trying to hook into an existing system), then you will need to decide upon a suitable format. Although we have used JSON to encode our array into a string in the example above, you could also use PHP’s `serialize()` and `unserialize()` functions if you knew you would only be sharing the data with other PHP scripts. However if you think your software may be interacting with programs written in another language in the future, sticking to language independent encodings like JSON or XML is a wiser choice.

Although it should be obvious, remember that any data in memory is volatile. It won’t be there if your system crashes, if the memory segment is deleted (usually when one or more programs exit), or after a reboot. Write anything critical to disk as well.

| ![information](Images/image00248.jpeg) || **Further Reading** SHMOP Shared Memory in the PHP Manual  

[http://php.net/manual/en/book.shmop.php](http://php.net/manual/en/book.shmop.php) |

| --- | --- |

| ![](Images/image00249.gif) || ***SimpleSHM*** |

| --- | --- |

|   ||   |

|   || An abstraction layer for `shmop` to simplify getting and setting shared memory |

|   ||   |

|   || ***Main website*** : [https://github.com/klaussilveira/SimpleSHM](https://github.com/klaussilveira/SimpleSHM) |

### 7.5 PHP message queues

Message queues provide an easy way for multiple processes to interact. At its most simple, one process adds messages to the queue, and another takes them off. The queue is maintained usually by a intermediate process or the OS itself. Queues make a programmers life easier than, say, messaging using shared memory as the programmer doesn’t need to worry (too much) about timing and synchronisation, and there are usually no need for locks. The sending process can fire off a message and forget about it (if it wants to), the receiving process can simply sit around and wait for a message to arrive (or do other things and check back for the messages later). There are a number of message queue APIs and extensions available to PHP, and we will look at most of those later in this chapter. In this section, we will look at the `sysvmsg` message queue which is part of the Semaphore extension that we looked at in the previous sections. This is a basic but useful message queue system, and has the advantage that it is usually compiled into most PHP distributions and it doesn’t require any third party APIs, daemons or libraries.

Lets jump right in with an example. We’re going to modify our random number generator scripts from the previous section to use a message queue. Our first script, `generator2.php` is going to fire off 20 messages, each with 3 random numbers, in quick succession and then exit. Our second script, `display2.php`, will pull those messages out at its own pace (1 per second) and display them.

*   This script is `generator2.php`

```
 1 <?
 2 
 3 $queue = msg_get_queue('1234456', 0666);
 4 
 5 for ($counter=0; $counter < 20; $counter++) {
 6 
 7 	$phpArray = array(rand(0,50000), rand(0,2000), rand(5000,100000));
 8 						
 9 	if (!msg_send($queue, 3, $phpArray, true, true, $errorCode)) {
10 
11 		 echo("Error - couldn't send message - code $errorCode\n"); 
12 
13 	};
14 
15 };
```

*   This script is `display2.php`

```
 1 <?
 2 
 3 $queue = msg_get_queue('1234456', 0666);
 4 
 5 while (1) {
 6 
 7 	sleep(1);
 8 
 9 	if (!msg_receive($queue, -4, $realType, 1024, $phpArray, true, 
10 		0, $errorCode)) {
11 			echo("Error - Couldn't receive message - code $errorCode\n");
12 	};
13 
14 	echo("Fetched message at ".date("H:i:s").". Random numbers are :\n");
15 
16 	print_r($phpArray);
17 
18 };
```

If you run `generator2.php` first, you will see it complete and exit almost straight away. You can then wait as long as you like before running `display2.php`, hours or days even, as the messages will happily sit there in the queue (unless you turn your computer off). When you do run it, you will see the random numbers appearing, one set every second. If you use `ctrl-c` to kill the script before it has read all 20, you can simply start it going again and it will pick up where it left off, until all 20 have been displayed. At that point, it will sit and wait for any new messages to appear on the queue. If you run `generator2.php` again in another terminal while `display2.php` is sitting and waiting, you will see `display2.php` spring into life again almost immediately and start displaying the new set of numbers we just generated.

So lets look at how these scripts work. They should seem similar to, but simpler than, the earlier shared memory examples. In each script, we first open the message queue with the `msg_get_queue()` function. This either creates, or if it already exists, opens the message queue. We supply it with a unique integer key as the first parameter to indicate which queue we want to use. See the notes on the `ftok()` function in the semaphore section above regarding generating unique keys. The second parameter is standard Unix permissions for the queue. The function returns a unique ID for the `$queue` which we use with the `msg_send()` and `msg_receive()` functions. This ID is an internal PHP resource ID and is different to the queue key we specified earlier.

In `generator2.php` we then generate a PHP array of random numbers as before, and we put this array into the queue with the `msg_send()` function. We do this 20 times in quick succession and then exit. This function takes a number of parameters:
