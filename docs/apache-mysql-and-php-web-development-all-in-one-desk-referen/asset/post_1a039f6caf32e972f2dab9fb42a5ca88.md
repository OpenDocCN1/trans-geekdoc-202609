
### Chapter 3: Ten Third-Party Packages That Enhance Security .....33

- Locking Down with Bastille .....33
- Linux Intrusion Detection with LIDS .....34
- Starting Easy with Guarddog .....34
- Taking Control with Firestarter .....35
- WinRoute Firewall .....36
- ZoneAlarm .....37
- Snort .....37
- ACID .....38
- Opening the Box: Pandora .....38
- Getting In with Nessus .....39

## Book II: Building an Apache Web Site .....41

### Chapter 1: Introducing the Apache Web Server .....43

- The Advantages to Using the Apache Web Server .....43
- Understanding How Apache Works .....44
- Communication between Apache and the browser .....44
- Receiving requests .....45
- Locating the requested file .....46
- Processing files as scripts .....47
- Using cookies .....48
- Taking a Look at the Apache Architecture .....49

### Chapter 2: Installing Apache .....51

- Getting Apache from the Web .....51
- Selecting a version of Apache .....51
- Selecting the type of file to install .....52
- Before installing Apache .....53
- Installing Apache from Source Files .....53
- Installing Apache from Binaries .....56
- Installation Options .....58
- Setting paths .....58
- Setting environmental variables .....60
- Enabling modules .....61
- Starting and Stopping Apache .....61
- Starting Apache .....62
- Using Apache start options .....62
- Restarting Apache .....64
- Stopping Apache .....64
- Troubleshooting Apache .....64
- Problems compiling Apache .....65
- Problems starting Apache .....65
- Running Multiple Apache Servers .....66

### Chapter 3: Configuring Apache . . . . . . . . . . . . . . . . 67

- Understanding Configuration Files . . . . . . . . . . . . . . . . 67
- Using Directives . . . . . . . . . . . . . . . . . . . . . . . . . 69
- Configuring the server . . . . . . . . . . . . . . . . . . . . . . 70
- Configuring log files . . . . . . . . . . . . . . . . . . . . . . . 73
- Running Scripts . . . . . . . . . . . . . . . . . . . . . . . . . . 77
- Configuring Directories and Files . . . . . . . . . . . . . . . . . 79
- Setting up a default directory . . . . . . . . . . . . . . . . . . 80
- Identifying directories . . . . . . . . . . . . . . . . . . . . . . 80
- Using directives with directories . . . . . . . . . . . . . . . . . 81
- Using directives with files . . . . . . . . . . . . . . . . . . . . 83
- Configuring Virtual Hosts . . . . . . . . . . . . . . . . . . . . . 84

### Chapter 4: Apache Modules . . . . . . . . . . . . . . . . . . . . 87

- Installing Modules . . . . . . . . . . . . . . . . . . . . . . . . . 87
- Compiling modules . . . . . . . . . . . . . . . . . . . . . . . . . 87
- Using base and extension modules . . . . . . . . . . . . . . . . . . 88
- Using external modules . . . . . . . . . . . . . . . . . . . . . . . 89
- Some Useful Modules . . . . . . . . . . . . . . . . . . . . . . . . 89
- PHP . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 89
- Secure Sockets Layer (SSL) module . . . . . . . . . . . . . . . . . . 89
- Perl . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 91
- Python . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 91

### Chapter 5: Ten Security Tips . . . . . . . . . . . . . . . . . . . 93

- Update Regularly . . . . . . . . . . . . . . . . . . . . . . . . . . 93
- Restrict Access to the Apache Directory . . . . . . . . . . . . . . . 93
- Don't Run Your Server as Root . . . . . . . . . . . . . . . . . . . . 93
- Monitor Server Requests . . . . . . . . . . . . . . . . . . . . . . . 94
- Use a Restricted Default Directory . . . . . . . . . . . . . . . . . . 94
- Don't Let Users See Your Files . . . . . . . . . . . . . . . . . . . . 94
- Limit CGI Scripts . . . . . . . . . . . . . . . . . . . . . . . . . . 94
- Don't Allow .htaccess Files . . . . . . . . . . . . . . . . . . . . . . 94
- Use suEXEC Carefully . . . . . . . . . . . . . . . . . . . . . . . . . 95
- Use SSL for Important Communications . . . . . . . . . . . . . . . . . 95

## Book III: Perl Web Site Automation . . . . . . . . . . . . . . . . 97

### Chapter 1: Introducing Perl . . . . . . . . . . . . . . . . . . . 99

- Trying Out a Simple Perl Program . . . . . . . . . . . . . . . . . . . 99
- Commenting your code . . . . . . . . . . . . . . . . . . . . . . . . . 101
- Keeping Perl on its toes with the -W option . . . . . . . . . . . . . . 102
- Ending a Perl program . . . . . . . . . . . . . . . . . . . . . . . . . 102
- Processing Text Files . . . . . . . . . . . . . . . . . . . . . . . . . 103
- Running as a CGI script . . . . . . . . . . . . . . . . . . . . . . . . 104
- Interacting with Web Servers . . . . . . . . . . . . . . . . . . . . . . 105
- Navigating the Perl Online Help . . . . . . . . . . . . . . . . . . . . 105

### Chapter 2: Simple Data Types ....................................................107

- Storing Data in Variables ....................................................108
- Storing Single Items as Scalars ............................................109
- Writing out variables ..........................................................110
- Putting special characters in strings ....................................111
- Writing strings and variables together ...................................114
- Storing Lists of Items .........................................................115
- Changing an item in a list .....................................................117
- Embedding list elements in a string .......................................117
- Obtaining slices of a list .......................................................118
- Putting slices into individual variables ...................................119
- Associating Data with Hashes .................................................121
- Understanding Scalar Context and List Context ...........................122

### Chapter 3: Comparing and Testing Variables ................................125

- Testing Conditions .................................................................125
- Performing Actions Based on Conditions ....................................129
- Making Consecutive Comparisons ..............................................130
- elseif ................................................................................130
- switch .................................................................................131
- Comparing in Different Ways ....................................................133
- Performing Comparisons Together ..............................................136

### Chapter 4: Controlling the Structure of Your Program ......................137

- Looping ...................................................................................138
- Looping for each item in a list: foreach loops ............................138
- Looping for a reason: for loops .................................................141
- While my loop gently runs: while loops ......................................142
- Until the end of time (or a condition happens): until loops .............144
- Doing something at least once: do-until loops ...............................145
- Breaking out of or continuing with a loop ....................................146
- Subroutines ............................................................................148
- Passing data to a subroutine ......................................................150
- Passing multiple parameters to a subroutine ................................151
- Keeping variables local to the subroutine ....................................152
- Returning data to the caller .......................................................154

### Chapter 5: Processing Text Files and Directories ............................157

- Processing Directories ..............................................................158
- Getting and setting the working directory ...................................158
- Obtaining a directory listing .....................................................158
- Recursively listing a directory ...................................................160
- Processing Files ........................................................................161
- Opening a file specified as a command-line argument .....................161
- Chopping your lines ...................................................................162
