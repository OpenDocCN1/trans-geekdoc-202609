# REMOTE DESKTOP SERVICES

There are several complications to consider when dealing with Remote Desktop Services and roaming profiles:

+   It is a bad idea to mix a user's desktop roaming profile with the profile that will be used on a Remote Desktop server/virtual desktop because registry settings and shortcuts from the different systems will be mixed.

+   You may employ the concept of "application silos" in a Remote Desktop server farm; in other words, Server1 and Server2 might have BizzApp installed, but Server3 might not. You don't want shortcuts for BizzApp to appear when a user is logged into Server3 with a roaming profile.

+   A common use for Remote Desktop services is to share applications from client with users in branch offices. You do not want branch-office roaming profiles to load across the WAN, but you do want some roaming profile solution.

You can apply this Group Policy object to disable roaming profiles on the machine:

**Path** the is Computer Configuration\Administrative Templates\System\User Profiles.

**Entry** the is "Only allow local user profiles."

**Description** Disable the usage of roaming profiles on this computer
This is a crude solution. It turns off the ability to download a roaming profile and returns you to a scenario where the user does not have a consistent working environment.
Alternatively, you configure users with specific roaming profiles for farms of machines. For example, when a user logs into a Remote Desktop server farm, they will use a dedicated profile from a Remote Desktop server roaming profile share. When they log into their PC, they will use a dedicated profile from a PC roaming profile share. When they log into their virtual desktop, they will use a dedicated profile from a virtual desktop roaming profile share.

Table 26.3 Remote Desktop Services Profile GPO
| PATH | ENTRY | DESCRIPTION |
|---|---||
| Computer Configuration\Administrative Templates\Windows Components\Remote Desktop Services\Remote Desktop Session\Profiles | Set path for Remote Desktop Services roaming profile | You can specify the profile of a user account when logging in via Remote Desktop. This takes precedence over all profile settings. You can use %username% to allow multiple profiles or simply use one folder for all users. |
| Computer Configuration\Administrative Templates\Windows Components\Remote Desktop Services\Remote Desktop Session\Profiles | Use mandatory profiles on the Remote Desktop session host server | When enabled, this turns the profile specified in the previous GPO setting into a mandatory profile. |