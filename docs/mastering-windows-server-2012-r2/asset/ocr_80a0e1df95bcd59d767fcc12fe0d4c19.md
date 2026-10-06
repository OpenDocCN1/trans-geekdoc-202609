# MANAGING ROAMING PROFILES

Speaking of disk space, you might want to consider how big a roaming profile can get. For example, users could upload their entire MP3 collection into My Music. It might be an innocent action where they think they're only consuming local storage. These are roaming profiles; 1000 users all doing something like this adds up to terabytes of storage being consumed on the organization's file servers with nonbusiness data. Should the organization be paying for this?

The solution is to use machine and Group Policy objects to control how roaming profiles behave in this and other circumstances.

# Machine Settings

You'll now look at how you control roaming profiles on a per-machine basis using Group Policy. Every user logging onto a machine inheriting the Group Policy settings that you configure be set by these settings.

# CLEANING UP PROFILES

If you, you'll find that a locally cached profile is created and kept on the workstation for the Remote Desktop profile. When you think about, it probably makes no sense to keep a copy of it in environments where you are using a mandatory profile.

Even if you're not using mandatory profiles, you might want some way to clean up older profiles when a computer reboots. Group Policy gives you some tools to do this (see Table 26.1).

| PATH | ENTRY | DESCRIPTION |
|---|---|---|
| Computer Configuration \Administrative Templates\System\User Profiles | Delete cached copies of roaming profiles | Locally cached copies of a roaming profile will be deleted when the user logs out |
| Computer Configuration \Administrative Templates\System\User Profiles | Delete user profiles older than a specified number of days on system restart | Profiles older than a specified number of days will automatically deleted when a computer restarts. |

# MULTIPLE SETTINGS AND ROAM PROFILES

What do you do with a user who has a roaming profile and that travels between branch offices across the world? By default, the user logging in will measure the network speed between itself and the location where the profile is stored. If the link is considered too slow, then the profile will not be downloaded. Instead, the user will be offered a temporary local profile. However, remember that this won't work with super mandatory profiles. You can control this measurement process works using GPO (see Table 26.2).