# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

+   3. Configure the template user's profile, and log out.

+   4. Log into the computer as an administrator,Netlogon, and copy the template user's profile to \<Active Directory Domain Name>\Netlogon\Default User.V2.

In the chapter's example, this would be \bigfirm.com\Netlogon\Default User.V2. Notice the .V2 extension. This signifies version 2 profiles for Windows 8 and Windows Server 2012 or newer.

+   5. Make sure that the Authenticated Users group is permitted to use this new profile when you copy it.

+   6. Check out the process you used to copy and assign permissions to profiles earlier in this chapter.

This default network profile will be copied to every new user on the network. The flaw with this solution is that user configuration for a user includes things such as regional settings. Consider an organization where are branch offices in foreign countries. These users will probably need different regional settings to match their keyboard and so on. It'll a bit of a pain to change these settings for the user when they first log in. You also need to be careful about keeping location-specific settings for a file server in New York and have someone logging in at the San Francisco office 3000 miles away to have a file server that's appearing to be very slow.

You cannot have a "roaming" default profile. The profile can be stored only in a specific folder. And this folder is copied to all domain controllers via SYSVOL replication.

Default network profiles are fine for simple networks where everyone shares the same basic configuration. You should think long and hard about deploying default network profiles in more complex networks where users require different basic configurations such as regional settings. The, user can change settings when they first log in, but that generates lots of help-desk tickets. You might want to look at an automated configuration. You could use a GPO to define regional settings after a user has logged in, but this locks a user down. A common experience is that not everyone has the same configuration in an office in this environment. Instead of default network profiles, a scripting or Group Policy solution will make those localized configurations when a user logs in for the first time. This allows few users who are not norm to their own configuration and retain those settings.

# Managing Roaming Profiles

Roaming profiles require considerable thought if you have different operating systems, users roaming between branches with limited network links, and Remote Desktop Services. You can do some advanced management of profiles using Group Policy, as you saw earlier when granted rights to automatically generated profiles to administrators.

Let's look at a few examples where you might have issues. If you have a farm of Remote desktop servers, then a user could log into any of them. Users logging into 10 servers, you could end up with 10,000 cached roaming profiles. That's a lot of disk space wasted