# JOINING THE DOMAIN

be added to an unattended answer file in order to join a computer to a domain (offline) as part of the OS installation.
One about the blob: if you provision the computer account in AD using djoin.exe and then open the resulting text file to read it, you will be disappointed because it's not human-readable. However, it contains sensitive data, as as the machine account password and other important domain information.

These are the steps to join an offline computer to the domain:

+   - Run djoin on a Windows 8 or Windows Server 2012 machine that can communicate with the DC.

This will create a computer account in AD for the computer name specified and create the text file used in step 3.

+   - Move that djoin on the offline client computer (securely).

+   - Run djoin on the offline machine, and import the text file.

# djoin Requirements

You can run djoin only on Windows 7 and Windows Server 2012 computers. It's possible to use djoin to join a Windows 8 or Windows Server 2012 computer to a down-level DC (via the /downlevel parameter, but the example in this will join a Windows 8 client to a Windows Server 2012 domain.

There are few other requirements as well. First, the user who runs djoin on the provisioning machine must have the right to add computers to the domain. Domain users who have this permission although they can add up to 10 computers to the domain by default.

You should also be familiar with the djoin parameters to understand the commands issued in the following example. Table 18.1 describes these parameters.

# TABLE 18.1: djoin Parameters

| PARAMETER | DESCRIPTION |
| --- | --- |
| /provision | Creates the computer account in Active Directory |
| /domain | Specifies the domain the computer will be joining |
| /machine | Specifies the name of the computer that will be added to ADDS and that you want to join the domain |
| /savefile <filepath> | Specifies the name of the file to save the provisioning metadata |
| /dcname (optional) | Specifies the name of a specific DC you want to use to create the computer account |
| /reuse (optional) | Reuses an existing machine account (the machine account password will be reset) |
| /downlevel (optional) | Provides support for using a DC that runs Windows 2008 or older |
| /printblob (optional) | Creates a blob encoded for use in an unattended answer file |
| /defpwd (optional) | Uses the default machine account password—not recommended |