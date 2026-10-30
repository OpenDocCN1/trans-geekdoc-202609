# Shell Commands

Chapter 9 introduced a number of Linux shell commands. In this chapter, we will look at shell commands that are of interest to both attackers and penetration testers. Of course, some of these commands will require root privileges, but if the attacker or tester can get root privileges, there are many interesting things he or she can do.

# touch

The **touch** command is used with files. If you type **touch filename** and no such file exits, then a file with that name will be created. But the really interesting part of **touch** comes with files that already exist.

**touch -a** says to change the access time of a file. **touch -m** changes the modification time. Or you can even set one file to have the same times as another file. So **touch -r fileA fileB** will tell fileB to use all the timestamps from fileA.

If you don’t provide specific times (for example to **-a** and **-m**), those will be changed to current time. Or you can change them to any time you wish:

```
touch -d '1 May 2018 10:00' fileA
```

In Figure 10-4 you can see the file properties for test.txt.

![](bbox=[0.07, 0.51, 0.55, 0.84])

FIGURE 10-4 File Properties for test.txt.