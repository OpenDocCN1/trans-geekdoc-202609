# Configure Clients

27. Click Database Server in the left window.

28. Click the FileMaker Clients tab.

29. Set the number of FileMaker Pro client users that you want to be able to access your FileMaker databases on the server. The recommended number is approximately 10% more than the estimated number of peak users. This limits the total number of open threads, which can dramatically improve performance. Therefore, just because you can set the number of connections to 250 (or unlimited for FileMaker Server Advanced), does not mean that you should do so—that's just being a lazy administrator.

30. If you want to click idle users out of your database you can check the box for maximum idle time and set the number of hours and minutes.

25. Click Save.

![](bbox=[0.104, 0.335, 0.895, 0.655])

Figure 3-1: FileMaker Pro Client Configuration

# Configure Databases

31. Set the number of files (databases) that you want to host on the server. I recommend that you set the number to n+1 where n is the number of files on the server. That allows you to add a new database to the server and not have to scratch it for a few minutes trying to figure out why it won't open. Again, you can set the server to host 125 files, but that is simply wasting the performance of the server and is a clear indication of a lazy administrator.

32. Set the RAM allocation for FileMaker Server. In a single-server development environment where you might be running quite a few applications you may want to set FileMaker Server to the minimum of RAM – 64