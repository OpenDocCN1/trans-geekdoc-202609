

*   killing the terminal won’t kill our child process

*   we are truly running in the background

*   To dissociate (detach), we need to :

    *   move the child process into it’s own POSIX process session

    *   fork it once again (into the grandchild process) and kill the child process

    *   close any file descriptors such as STDIN that may tie it to the terminal

Once all this is done, you will be returned to the command prompt in the terminal (assuming thats where you started your original parent process from) and your (grandchild) daemon will be running on its own. You will only be able to interact indirectly with your daemon from now on. Finally, assuming that the daemon is to run continuously (or for a set period of time) rather than just completing a task and exiting, the process will need to enter a loop where it will continuously cycle and, for instance, await events or perform continuous tasks. Its probably also wise to give it the ability to exit upon demand.

This may sound quite a long and involved process, however it is fairly straight forward in PHP. The following script follows this process and outlines the basics.

```
  1 <?
  2 
  3 # We start by forking this script, which creates the child process.
  4 
  5 $pid = pcntl_fork();
  6 
  7 # The child process will start running from here and will be a copy of the
  8 # parent process, which includes all opened resources, variable values and
  9 # so on, with the sole exception of the $pid variable above which is not
 10 # set for the child. The parent process will keep running from here as 
 11 # well, with the process ID of the child process assigned to $pid
 12 
 13 # If for some reason a child process could not be forked, for example 
 14 # the system is low on memory, $pid will be set to -1
 15 
 16 if ($pid == -1) { exit("Could not fork the child process"); };	
 17 
 18 # If $pid is set to a process ID, then we must be the parent, and 
 19 # should exit.
 20 
 21 if ($pid) { exit(0); };
 22 
 23 # As the parent has exited above, the following code is now executed 
 24 # solely by the child process. 
 25 
 26 # We detach from the TTY (terminal) by becoming the "session leader" 
 27 # (instead of the TTY being leader. This starts a new POSIX session) ...
 28 
 29 if ( posix_setsid()  === -1 ) { 
 30 	exit("Could not become the session leader"); 
 31 };
 32 
 33 # ... and then by forking again, to create a grandchild process
 34 
 35 $pid = pcntl_fork();
 36 
 37 if ($pid == -1) { exit("Could not fork child process into grandchild"); };
 38 
 39 # Exit the child process, leaving only the grandchild beyond this point.
 40 
 41 if ($pid) { exit(0); };
 42 
 43 # Now to finally dissociate from the TTY and run in the background, we 
 44 # need to close our input and output streams to it. These are 
 45 # automatically defined and opened in the CLI SAPI, so will always need to
 46 # be closed.
 47   
 48 if (!fclose(STDIN)) { exit('Could not close STDIN'); };
 49 if (!fclose(STDERR)) { exit('Could not close STDERR'); };
 50 if (!fclose(STDOUT)) { exit('Could not close STDOUT'); };
 51 
 52 # STDOUT is now closed, if you echo or print anything or interpolate HTML
 53 # after this point, your script would crash. Likewise, any error messages
 54 # would have nowhere to go, and any inadvertent attempts to read input
 55 # would end badly. So instead we will recreate these three streams, but 
 56 # with sensible destinations. When we fclose the standard streams, and
 57 # because you cannot redefine a constant, PHP simply assigns the standard
 58 # streams to the next three new file descriptors opened (whatever they 
 59 # are called and whereever they point to). Thus the following also acts
 60 # to protect any other streams you may open from "pollution" caused by
 61 # accidental writes to those standard streams
 62 
 63 $STDIN = fopen('/dev/null', 'r');
 64 $STDOUT = fopen('/dev/null', 'w');
 65 $STDERR = fopen('/var/log/our_error.log', 'wb');
 66 
 67 # We are now a free-floating daemon, fully detached from our TTY!
 68 
 69 # Now we go into our main loop, and do something useful.
 70 
 71 # We set a variable which will allow us to escape from the loop if we 
 72 # want to shut down our daemon.
 73 
 74 $stayInLoop = true;
 75 
 76 while ($stayInLoop) {
 77 
 78     # do useful stuff here, like listening for connections, 
 79     # monitoring things, or whatever else your daemon does.
 80    
 81     # When it's time to exit, set $stayInLoop = false at some point in the
 82     # loop and this loop will be the last. If you need to exit before the 
 83     # loop finishes you will need to call break and do any necessary 
 84     # tidying up. Here, we will end if it's a Tuesday, looping only once. 
 85 
 86     if (date('l') == 'Tuesday') { $stayInLoop = false; };
 87 
 88     # For this example, we're going to execute a cli program called 
 89     # notify-send to periodically pop up a notification to say hello.
 90 
 91     `notify-send 'Hello, The daemon is alive!'`;
 92 
 93     # The following line adds a "sleep" to each cycle of the loop. If we 
 94     # didn't do this, our daemon would (try to) consume 100% of the CPU 
 95     # time as it constantly cycles and evaluates the conditions for 
 96     # looping. You can adjust the time it sleeps for depending on the 
 97     # "responsiveness" required of your daemon. Giving it a break for even
 98     # a few 100 or 1000 milliseconds (using usleep) helps to maintain 
 99     # overall system responsiveness.
100     
101     sleep(15); # Loop every 15 seconds
102 };
103 
104 # We've exited our loop, so do any clean-up required here
105 
106 `notify-send 'The Daemon is now finished. Bye Bye.!'`;
107 
108 # And then exit
109 
110 exit(0);
```

The code above, while it doesn’t do anything particularly useful, is an outline of the basic steps involved in creating a PHP daemon and shows how simple it can be. You can combine it with the other techniques outlined in this book to create some useful systems and networking tools that run permanently in the background.

There are a number of important things to bear in mind when writing daemons in PHP, to ensure they keep running as expected.

Firstly, when you fork a process as we have done to create a child process, the child is an almost exact copy of the parent, including the state of variables and resources. This means that if you do anything in the parent script before forking, it will be replicated in the state of the child. A common gotcha, particularly if forking multiple daemons from the same script, is setting up database connections in the parent before forking. The children will then share the same resource identifier (i.e. exactly the same connection) as the parent and the other children, and as soon as one of them closes the connection (e.g. by exiting) the database will become unavailable to all of the others. On the other hand, this doesn’t apply to, say, variables. If you set the variable `$foo = 6;` in your parent, when each child starts `$foo == 6` will be true, but if you alter it in one child, it will not alter in the others, as they are separate variables (just set to the same value at the start). Technically the resource identifiers in the database example are a also separate identifiers in each child, they just happen to point to exactly the same external database connection.

