+   - **/var/log/mysql.***: This log records activities related to the MySQL database server and will usually be of less interest to a computer crime investigation.
+   - **/var/log/apache2/***: If this machine is running the Apache web server, then this log will show related activity. This can be very useful in tracking attempts to hack into the web server.
+   - **/var/log/lighttpd/***: If this machine is running the Lighttpd web server, then this log will show related activity. This can be very useful in tracking attempts to hack into the web server.
+   - **/var/log/apport.log**: This records application crashes. Sometimes these can reveal attempts to compromise the system or the presence of a virus or spyware.
+   - **/var/log/user.log**: These contain user activity logs and can be very important to a criminal investigation.

# # Getting Back Deleted Files

It is a fact that criminals frequently attempt to destroy evidence. This is also true with computer crimes: Criminals may delete files. However, there are a variety of tools you can use to recover such files, particularly in Windows. DiskDigger is a free tool that can be used to recover Windows files. This is a very easy-to-use tool. There are more robust tools, but the fact that this is free and easy to use makes it perfect for students learning forensics. Let’s walk through its basic operation. It should be noted that all the aforementioned forensics tools will recover deleted files for you. It must also be noted that there are many file recovery tools available on the Internet. DiskDigger is simply shown as an example of what is available.

On the first screen, shown in Figure 14.8, you select the drive/partition you wish to recover files from.

![](bbox=[0.143, 0.456, 0.599, 0.716])

On the next screen, you select the level of scan you want to do. This is shown in Figure 14.9. Obviously, the deeper the scan, the longer it can take.