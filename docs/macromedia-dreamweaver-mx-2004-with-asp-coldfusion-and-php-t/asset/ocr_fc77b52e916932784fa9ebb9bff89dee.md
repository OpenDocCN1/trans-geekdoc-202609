By right-clicking the traffic light, and choosing Show Me, you can see the WinMySQLadmin console, which provides information about MySQL and which can be used to specify various configuration options.

![](bbox=[0.27, 0.145, 0.93, 0.475])

Now that you have installed MySQL and started it, you can create and populate the Newland ‘Tours database and begin using it for site development.

+   6) Copy newland_tours.sql from the Lesson08\Start folder to the C:\mysql folder on your hard drive.

The exact location of the file doesn’t matter too much, but in a moment you’ll have to type its path, so it’s best to copy it into an easily accessible directory.

+   7) Using Windows Explorer, navigate to C:\mysql\bin, and double-click mysql.exe to open the mysql command prompt.

‘The mysql> prompt appears.

+   8) At the mysql> prompt, type the following to generate the newland_tours database in your copy of MySQL. Press Enter.

```
source C:\mysql\newland_tours.sql
```