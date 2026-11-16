Having removed any services, let's look at the ones we do need. For example, our server needs to serve web pages to the clients. Also, as an administrator we need remote shell access and remote FTP access.

For now, let's leave the fact we need to serve web pages, and look at remote shell and remote FTP access. It is insecure to use the default telnet daemon and default FTP daemon, since these allow the unencrypted username and password to be transferred over the Internet. Instead, we can use a secure shell. This will allow us to administer and transfer files to the server over an encrypted link.

The first thing to do is to install the secure shell daemon. It is recommended that one of the two available from http://www.ssh.fi/ or http://www.openssh.org/ is used. Having installed and tested the secure shell daemon, it is best to disable the FTP and telnet daemons as well.

> A common denial of service attack is to try to fill up the hard drive with useless junk, normally temporary files, to try to get the server to crash. To avoid this happening you should ensure that /tmp and /var are on separate partitions, so if /tmp does get filled there is still room on the /var partition so that core services can continue to function.

# # Monitoring the System

The best way to keep an eye on the system is to look at the server's log files. If you notice something abnormal then look into the log entry further and find what caused it.

It is possible to automate the log file monitoring to a certain extent using scripts that parse the log files and get rid of the meaningless log file entries. We develop a simple command line script that does this in Chapter 20. This mail_stats.php script can be modified to parse the other log files that our applications create.

It is also important to look at the other monitoring tools, such as Tripwire. Tripwire is an application that helps ensure the integrity of critical system files and directories, by identifying all changes made to them. We can configure Tripwire, such that if one of these files is changed we receive an alter notification via e-mail. Alternatively, we can set it up as a cron job to check the integrity of each of the files Tripwire watches. Also, Tripwire can help recover from an intrusion, as it keeps track of the files that an intruder changes so we know which files must be restored to repair the system. Some good resources on Tripwire are listed in the Resources and Further Reading section, at the end of this chapter.

# # Monitoring New Vulnerabilities

One difficult thing about dealing with security is that, the people who are trying to break into the system are constantly thinking up new ways to do it, and finding new vulnerabilities in various pieces of software that allow them to do it. This means that part of the security policy should be to monitor various mailing lists where these new vulnerabilities and the patches to fix them are posted. Two good ones are Bugtraq and Packet Storm.

It is important to react quickly to new vulnerabilities posted on these lists. We should first check if the system needs upgrading or patching and react accordingly. Normally, when a vulnerability is posted, the vendor of the software will post a patch at the same time.