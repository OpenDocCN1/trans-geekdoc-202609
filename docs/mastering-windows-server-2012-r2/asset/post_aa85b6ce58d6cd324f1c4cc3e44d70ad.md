
[content]
# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

# FIGURE 26.9
Checking the user object home directory setting

![](img/41a83208e6906a3732620203b836cea7_1313_0.png)

Here's the cool bit: Windows creates the folder and sets the correct permissions for you on your file server. This is visible on the file server, as shown in Figure 26.10.

# FIGURE 26.10
The automatically created home directories

![](img/41a83208e6906a3732620203b836cea7_1313_1.png)

You can see in Figure 26.11 that the home directory for each user has inherited the permissions on the Home folder. Each user has been granted Full Control permissions over their own folder:

| Group | Permission |
|---|---|
| BF2\Administrators | Full Control |
| System | Full Control |
| BigFirm\<User> | Full Control |

**FIGURE 26.11** The home directory automatically created permissions

![](img/41a83208e6906a3732620203b836cea7_1314_0.png)

All of the work is done! It's that. You can now log on using one of these users. In our lab, JBlogs will log into Windows, and the Z drive will be mapped to JBlogs' own home directory. Thanks to the permissions that are on each folder, the user in question cannot access a home directory that is owned by somebody else.

# SHARING HOME DIRECTORIES

We previously mentioned that some organizations choose to give users other than the owner access to home directories. You can add that access easily by adding Authenticated Users to D:\Shares\Home. This permission will be inherited by every home directory. You can give them Read & Execute, for read-only access, or you can give them Change rights so that they can modify the contents of another person's home directory.

# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

Some organizations choose to not configure the user object's Home Folder attribute. Their opinion is that it is easier to map the drive using a logon script. A logon script runs every time a user logs in and runs a set of commands. You'll look at them later. Alternatively, you can leverage Group Policy Preferences for drive mappings. If the drive moves to another server, it's easy to change a single logon script command or group policy instead of changing hundreds or thousands of users.

The counter opinion is on this that you have made your solution for home directories dynamic by using a DFS namespace to abstract the physical location of the share. You can share, and all users will retain their mappings once you modify the single folder mapping in the DFS namespace. In addition to this, some environment variables for the user's home are available when you set up the Home Folder attribute:

- HOMEDIVE: Represents the letter used to map the home directory, for example, Z:
- HOMEPATH: the path within the HOMEDIVE where the home directory is contained, for example, the path is %HOMEDIVE%\HOMEPATH% or Z:\
- HOMESHARE: the UNC path to the user's home directory, for example, \\bigfirm\com\BigShares\Home\Blogs

# Home Directory vs. Local Storage

You have given your users a centralized storage mechanism. You should consider communicating to your users that data should be stored on this drive and not on the local drive of the device. You can use Group Policy to enforce this policy. The following are keys to success:

- Communicate that home directories are backed up and that devices are not. There is no service-level agreement for data stored on devices.
- Enable the Volume Shadow Copy Service on your file servers, and educate users how to use the Previous Versions client to recover their files.
- Data on the device may not be secure. Educate the users about the need for data security.
- Using auditing where Required Rights Management Services to allow users to control at the file level who can see or edit a file.

You will look at some automated mechanisms little later that will further encourage users to keep data on the server instead of the device.

This section discussed how to allow a user to make their personal data available to them no matter what server or device they log into. We'll now cover roaming profiles and discuss how they can do the same thing with their working environment.

# Creating Roaming Profiles

A profile is a folder that contains all the settings pertaining to a user's working environment. By default, the profile is stored in the C:\Users directory. A roaming profile is stored on the network instead of the local drive of the machine where the user logs in. However, it is cached locally by default. The advantage of a roaming profile is that a user can log into any machine in the domain and have a consistent working environment. However, you have to watch out for the profile containing information that is specific to a computer, application, or operating system that won't apply to all machines that the user might log into. A profile has two types of content:

- Files and folders
- ntuser.dat

A user's Windows and application settings are usually stored in HKEY_CURRENT_USER in the registry. This needs to be available to the user every time they log in. It is stored in a file called ntuser.dat.

Other types of content are stored as files in specially named folders:

- My Documents
- My Music
- Favorites
- AppData
- Desktop
- Contacts

A user's Windows and application settings are usually stored in HKEY_CURRENT_USER in the registry. This needs to be available to the user every time they log in. It is stored in a file called ntuser.dat.

Other types of content are stored as files in specially named folders:

- My Documents
- My Music
- Favorites
- AppData
- Desktop
- Contacts

A solution to this problem is the roaming profile. The concept is that the user's profile is stored on a share that is similar to the one you've set up for home directories. The profile is downloaded from the file server whenever a user logs in. It is cached in C:\Users on the computer the user logs into. The contents of the profile that have changed are saved back to the file server when the user logs out. That can sound like a lot of files moving around the network. It can be, however, Windows will download or upload only those that need to be downloaded or uploaded. Let's look at two ways to create roaming profiles. One is very quick and easy to set up. The second takes a little further by increasing security, but it does require a little more work.

# Creating Roaming Profiles: The Easy Way

We'll go through the process of configuring roaming profiles for the users in BigFirm. With this approach, you will set up the profile settings in the user objects. Unlike the easy approach for setting up home directories, a folder will not be created for you set up the roaming profile attribute. Instead, the user's roaming profile will be set up automatically when the user logs in.

You'll start by using an approach recommended by Microsoft that allows for the easy deployment of profiles. You will create a file share on BF2, the file server.

1. Create a folder called Profiles in D:\Shares, as shown in Figure 26.12.
