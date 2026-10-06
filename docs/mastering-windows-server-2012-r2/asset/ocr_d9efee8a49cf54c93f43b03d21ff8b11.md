The second set of settings in 26.3 allows you to tell the computer to treat any roaming profile as a mandatory profile, that is, to never save any changes made by the user. This is an alternative to the previously described method for creating a mandatory profile.
For Windows Server 2012, you will find these GPO settings in Computer Configuration\Administrative Templates\Windows Components\Remote Desktop Services\Remote Desktop Session Host\Profiles.

# SPECIFYING A REMOTE DESKT SERVICES PROFILE

There is an option in the user account to specify a Remote Desktop Services profile. That's a rather simple solution that implies there will only ever be one profile for that that is suitable for all Remote Desktop servers. This might be better for smaller organizations with one or two Remote Desktop servers. We recommend that you think long term and adopt the GPO approach to manage Remote Desktop Services roaming profiles.

You will need to clean up cached profiles (earlier in the chapter) if you are using roaming profiles on your Remote Desktop servers. You can quickly reap a lot of space on your system if left unmanaged.

# ADDITIONAL ROAMING PROFILE GPO SETTINGS

You've seen only half of the GPO settings you can use to configure roaming profiles. Table 26.4 shows the rest.

Table 26.4 Miscellaneous GPO settings for roaming profiles
| PATH | ENTRY | DESCRIPTION |
|---|---|---|n| Computer Configuration\Administrative Templates\System\User Profiles | User management of sharing name, Account pictures and domain information with apps | Allows app to have access to the-username, account picture, and domain information. |
| Computer Configuration\Administrative Templates\System\User Profiles | Set user home folder | You can configure the user's Home folder here instead of the account. |
| Computer Configuration\Administrative Templates\System\User Profiles | Set the schedule for background upload of a roaming profile's registry file while user is logged on | You can configure a schedule to regularly upload the NTUSER.DAT file to the server in the background while the user is logged in. |
| Computer Configuration\Administrative Templates\System\User Profiles | Do not check for user ownership of Roaming Profile Folders | By default Windows checks for user ownership of the profile before downloading it. This policy can reverse this practice. |