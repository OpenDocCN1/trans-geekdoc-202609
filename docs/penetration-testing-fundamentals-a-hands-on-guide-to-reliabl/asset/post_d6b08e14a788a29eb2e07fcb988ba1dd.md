
can also find Linux distributions that are specifically for firewalls such as IPCop and FireGate Server. It would not be an exaggeration to say that there is a Linux distribution for almost any purpose you might have. And of course there is Kali Linux, a favorite in the penetration testing community.

## Linux Commands

While the history of Linux is interesting and may put your understanding of Linux in context, the real goal of this chapter is to enable you to work with Linux. That means using Linux commands. In this section we will explore the basic Linux commands.

### ls Command

ls is one of the more elementary commands. It simply lists the contents of the current directory you are in. You can think of it much like the dir command in Windows. You can see this command in Figure 9-1.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_229_0.png)

FIGURE 9-1 Listing Directory Contents with ls Command.

Every command in Linux (or Windows for that matter) has flags. These flags allow you to modify the command to produce some different result.

The easiest way to see these commands is to either type the command followed by -?, such as

```
ls -?
```

or use the term **man** (short for manual page) followed by the command, such as

```
man ls
```

The following are a few of the more common **ls** flags:

- **-a**: Shows you all files, even files that are hidden
- **-l**: Gets properties of files
- **-t**: Sorts by modification time

This is a very fundamental command you should be quite familiar with.

### cd Command

The **cd** command is used to change directories, to move either down or up the directory tree. It works very much like the **cd** command in Windows. The following are a few of the options with **cd**:

```
cd directoryname    // changes to the directory
cd ~                // changes to home directory for that user
cd ..                // changes up one level
```

This is another very fundamental command. Without a basic grasp of this command, you will have a very difficult time navigating folders in Linux. You can see this command in Figure 9-2.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_230_0.png)

FIGURE 9-2  Changing Directories with **cd** Command.

### Pipe Output

All shell commands, by default, display their output to the screen; however, there may be instances where you would prefer the output be stored in some file. That is where the redirect command (>) comes in. It causes the output from some other command to be redirected to a file. This is very useful, particularly for some of the system commands:

```
ls > myfile.txt
```

You can see this command shown in Figure 9-3.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_231_0.png)

FIGURE 9-3 Piping a Command.

### finger Command

The finger command is used to get information regarding a specific user. This is often useful for a system administrator. For example, if you run the top command and see that one specific user is spawning several processes on your server, and those processes are consuming resources, then you may want to find out about that user. This is shown in Figure 9-4.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_232_0.png)

FIGURE 9-4 Retrieving User Activity with finger Command.

### grep Command

The grep command is so popular with Linux and Unix users because it is so flexible. If you type in man grep at the shell, you will see a rather extensive entry, listing a number of flags you can pass to grep. One small section, in one chapter of a book, could not possibly do justice to the versatility and flexibility of this command. However, I can provide you a basic introduction to grep.

Find all instances of the word “virus” in a file named somefile:

```
grep 'virus' somefile
```

Look for the same data in the same file, but ignore case:

```
grep -i 'virus' somefile
```

Look for words beginning with v and ending with s in file somefile:

```
grep 'v...s' somefile
```

In this case the ... tell Linux how many letters to search for. To search, regardless of the number of intervening letters:

```
grep 'v.*s' somefile
```

The following command counts the number of accounts that have /bin/false as the shell:

```
grep -c false /etc/passwd
```

If grep finds a result, then it displays that line from the text file. If it does not find a result, then it displays blank. You can see some basic grep examples in Figure 9-5.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_233_0.png)

FIGURE 9-5 grep Examples.

### ps Command

The ps command is related to system processes, and is probably the most basic process-related command. It will provide you with a list of the current processes running on your system. With no options, ps will list processes that belong to the current user and have a controlling terminal. By default, ps selects all processes with the same user ID as the current user and associated with the same terminal as the invoker. It displays the process ID (PID), the terminal associated with the process (TTY), the cumulated CPU time in dd-hh:mm:ss format, and the executable name. Output is unsorted by default. However, as with so many shell commands, this one has a number of options you can pass to it in order to alter its behavior. Here are the more commonly used options:

- **-A**: Displays all processes; this is identical to the **-e** option explained below.
- **-N**: Displays all processes except those that fulfill the specified conditions.
- **-a**: Displays all processes with a TTY except session leaders and any process not associated with a specific terminal.
- **-d**: Displays all processes, but will omit session leaders.
- **-e**: Displays all processes on this system regardless of user or terminal.
- **-T**: Displays all processes on this terminal.
- **-x**: Displays processes without controlling TTYs.
- **-H**: Displays the processes in hierarchical format.
- **-w**: Displays the data in wide format.

You can see the **ps** command and the **ps -e** option in Figure 9-6.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_234_0.png)

FIGURE 9-6 Displaying All Processes with ps Command.

### pstree Command

The **pstree** command is very similar to the **ps** command except that it shows all the processes in the form of a tree structure (similar to how **tree** does it for directories). I personally find this view of running processes, shown in Figure 9-7, to be very useful, and I prefer it over the **ps** command.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_235_0.png)

FIGURE 9-7 Displaying Processes in Tree View with pstree Command.

As with most commands, this one has several options you may need to use:

- **-a**: Shows any command-line arguments.
- **-A**: Alters the display by using ASCII characters to draw the tree.
- **-c**: Disables compaction of identical subtrees. By default, subtrees are compacted whenever possible.
- **-G**: Causes the display to use VT100 line-drawing characters.
- **-h**: Displays the current process and its ancestors. If this terminal does not support highlighting, then it will simply display a normal pstree.
- **-H**: Works just like -h, except it highlights the specified process instead. Unlike with -h, pstree fails when using -H if highlighting is not available.
- **-l**: Causes the display to use long lines. By default, lines are truncated to the display width or 132 if output is sent to a non-TTY or if the display width is unknown.
- **-n**: Sorts processes with the same ancestor by PID instead of by name (numeric sort).
- **-p**: Causes the display to show PIDs. PIDs are shown as decimal numbers in parentheses after each process name.
- **-u**: Shows UID transitions. Whenever the UID of a process differs from the UID of its parent, the new UID is shown in parentheses after the process name.
- **-U**: Causes the display to use UTF-8 (Unicode) line-drawing characters.
- **-V**: Displays version information.

These options can be used to get additional information about the processes in the pstree.

### top Command

The top command is very much like the ps command except it lists the processes in the order of how much CPU time the process is utilizing. This can be very useful for an administrator, particularly if you are finding that your CPU utilization is high and you wish to identify the culprit. I personally also find the display to be far more informational than the ps display. I use the top command far more often than I do the ps command. You can see the top command in Figure 9-8.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_236_0.png)

FIGURE 9-8 Viewing CPU Time of Processes with top Command.

You should keep in mind that since this command lists processes by their CPU utilization, it is entirely possible to get different results if you run the command at different times. This command has a number of options that can alter the way it displays. In fact, it updates itself, so if you watch it you will probably see the items change.
