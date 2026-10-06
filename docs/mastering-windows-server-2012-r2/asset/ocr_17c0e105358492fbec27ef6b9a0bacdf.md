# CHAPTER 1 WHAT'S NEW IN WINDOWS SERVER 2012 R2

kind of device being used to connect. They wanted to make sure connecting through a WAN
or LAN (to virtual desktops, RemoteApp programs, or session-based desktops) provides a
experience to the user. Microsoft also wanted to make the remote desktop management
experience better. We agree that they made it better by adding a centralized console so
administrators can manage Remote Desktop Services from a single location.

You can read more about Remote Desktop Services in Chapter 17.

# Group Policy Object Improvements

What got better? Plenty. Managing Group Policy objects (GPOs) got easier with the built-in
Group Policy Management Console. In previous Windows versions, one problem that
administrators had was manually forcing a GPO to update. Even though GPOs automatically
ine 90 minutes, there are times when you need a GPO to take effect immediately.
Administrators had to remote to the specific computer and run gupdate.exe from the
command line to manually updating a GPO.

Now if an administrator wants to manually force a GPO update, the administrator can
use the context menu for an OU in the Group Policy Management Console and schedule
gupdate, exe to run on multiple computers at the same time. Administrators can also achieve
this by using the PowerShell utility and the new Invoke-GPUpdate cmdlet.
Here are some additional changes to Group Policy in Windows Server 2012 R2:

+   * When dealing with monitoring replication issues at the domain level, you no longer need
to download and run separate tools.

+   * For devices using RT, you can now configure local Group Policy. By default it
is disabled, and the service must be set to and to automate.

+   * Group Policy has been upgraded to support Internet Explorer.

You can read more about Group Policy in Chapter 9, "Group Policy: AD's Gauntlet and Active
Directory Delegation.".

# File and Print Sharing

Back before we ran web or email services on our Windows servers, we only used Server to
things: big drives and expensive printers. File and print are the oldest services offered\sby Microsoft networks, but apparently they're not too old to learn a few tricks.

# BranchCache

BranchCache is a technology that optimizes Windows bandwidth by copying content
either your main location or cloud server to your branch office. Once content is copied to the
branch, users can cache many rather than over the WAN. Having benefit to cache files
will conserve bandwidth and improve service. BranchCache can support any size office and
is not limited to how many times it can serve. BranchCache can be deployed with just a single
Group Policy object (GPO). This technology uses the Windows file server to divide files into
small encrypted pieces. The cool thing about dividing the files into smaller pieces is that
client computers can download only the pieces that changed. BranchCache will also check for
duplicate content and only download one instance of the content, saving disk space.