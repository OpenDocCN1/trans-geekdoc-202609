# Configuring Super Mandatory Profiles

There are some scenarios where you are using mandatory profiles but you cannot afford to allow anyone to be logged in if the mandatory profile cannot be downloaded for some reason, such as because of a network issue or a file server problem. When this be a realistic option? You're probably talking about something like a kiosk or a publicly accessible computer where it's better to have no service rather than a service that isn't tightly controlled.

So, it appears you need to find a solution for this scenario. Luckily, you have one in the form of super mandatory profiles. Implementing this solution isn't all different from implementing mandatory profiles.

Setting up super mandatory profile is just an extension of setting up a mandatory profile. Follow the previously described steps for configuring a mandatory profile, and then do the:

+   1. Rename the profile on the file server it has a .MAN.V2 extension; for example, rename Mandatory.V2 to Mandatory.MAN.V2.

+   2. Configure the .V2 component; for example, set the profile to \Bigfirm.com\BigFirmShares\Profiles\Mandatory.MAN.

+   3. Ignore the .V component to include the .MAN extension.

That's it! You've set a super mandatory profile for the user. The profile will act like a normal profile, not allowing any changes to be saved to the file server. However, unlike a normal profile, this user will not be to log in if the super mandatory profile cannot be downloaded.

There's an easy mistake that you can re-create to test this "no logon" functionality. Rename the NTUSER.MAN file in the mandatory profile to NTUSER.DAT. Now try to log on as. You'll be informed that the profile could not be downloaded and that the user cannot logon. Don't forget to rename the file to NTUSER.MAN when you're finished!

# Configuring a Default Network Profile

A default profile is used to build a user's profile if they don't already have one. Consider a user with no roaming profile configuration and logging in to Windows 8 or Windows Server 2012. Their new profile is created by copying the contents of C: \Users\default to the new profile folder in C: \Users\username.

There is a way for administrators to provide users with a customized default profile on the network. Domain members will automatically look for a default network profile. If one exists, this is used instead of the default profile that is stored on the computer. You would use a default network profile when you want to provide a preconfigured working environment for users. This seems like a mandatory profile, doesn't it? The difference is that the default network profile simply is copied to the user's own profile. The user is free to save changes to their own profile.

The process for creating a default network profile is very similar to the one you used for creating a mandatory profile:

+   1. Create a template user.

+   2. Log in as that user on a test computer.