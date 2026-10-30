But they can be combined; for example, 2 and 1 give write and execute permission. The full list of permissions follows. If you combine read, write, and execute, that would be number 7 (just total up the 1 for execute, 2 for write, and 4 for read).

+   - 0 – no permissions
+   - 1 – Execute only
+   - 2 – Write only
+   - 3 – Write and execute
+   - 4 – Read only
+   - 5 – Read and execute
+   - 6 – Read and write
+   - 7 – Full control

Now that you understand chmod and file permissions, it is time to execute our script. To execute this, or any other script, then from the shell type

```
bash myscript.sh
```

and your script will execute. In this case the script executes two specific shell commands: hostname and who. You can see it in Figure 10-10.

![](bbox=[0.07, 0.57, 0.8, 0.8])

FIGURE 10-10 Executing a Script.

Obviously, this is a pretty simplistic script, and of limited use. However, it does show you the basic techniques used to write a script and to execute it. This script has the proper identifier for what shell it is written for, a series of commands (albeit a short series), and the terminating/exit code. While this is a simple script, it does give you a template for how all scripts must be written.