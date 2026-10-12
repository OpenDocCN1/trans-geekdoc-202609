
But right now, you can see “Device status,” “User status,” and “Per-setting status.” The first two just tell you if the baseline at all has been delivered to a User or Computer group. The last report, “Per-setting status,” tells you if the setting you wished to apply actually got applied. There’s also a column called Conflict. The Conflict column is designed to tell you when there’s a collision between a device configuration profile and a baseline profile. Then you can tweak or remove the setting from one of the profiles.

The next logical questions of course are, Which profile should you tweak, and which profile should win? The answers are that you should go back and unwind the conflicting settings in the device configuration profile and use the setting within the baseline profile. This is a recommendation directly from the PM, Joey Glocke, when this feature was announced. But it makes sense to me, and I basically agree.

You can see both the announcement of this feature and the comment from Joey Glocke in the blog article here:

`https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-introduces-MDM-Security-Baselines-to-secure-the/ba-p/313442`

### Other resources

*   The official docs on Windows 10 Security Baselines with Intune can be found at:

    `https://docs.microsoft.com/en-us/intune/security-baselines`

*   Some more details on monitoring, reporting and troubleshooting can be found here:

    `https://docs.microsoft.com/en-us/intune/security-baselines-monitor`

*   The Group Policy–based version of the security baselines can be found at:

    `https://docs.microsoft.com/en-us/windows/security/threat-protection/security-compliance-toolkit-10`

*   A good blog entry with a walk-through and showing a conflict (and how to resolve it) can be found at:

    `https://osddeployment.dk/2019/01/27/start-using-intune-security-baseline/`

### VMware Workspace ONE and Security Baselines

Microsoft Intune isn’t the only MDM solution with baselines.

VMware Workspace ONE also has baselines. To see them as a Workspace ONE customer, go to `Devices ➢ Profiles & Resources ➢ Baselines` as seen here.

![](images/c10uf001.jpg)

Then you can use CIS benchmarks or a custom baseline.

CIS benchmarks are similar, but not exactly equal to what Microsoft is doing with its baselines. Some might say the CIS benchmarks are even more hard core.

You can also upload your own custom baseline, but doing so is a little cumbersome. The basic process is that you use the Microsoft `LGPO` tool (from the Security Compliance Toolkit) to suck out the policies of an existing machine’s local Group Policy store and store it as a ZIP.

Then, to perform the application of the policy, VMware Workspace ONE will drop the ZIP on the machine and “play back” the policy using, again, `LGPO`. `LGPO` must live in `%ProgramData%\Airwatch\LGPO` (how you get it there is up to you).

Note that this VMware Workspace ONE facility doesn’t have any way to do Group Policy Preferences or any easy way to make an update to your ZIP without first going back to the source machine, re-sucking out its brains, re-making the ZIP, and re-pushing it back out to machines.

That said, a video on the process can be found at `https://youtu.be/B5VzzhH0r20` from the one-minute mark to about the six-minute mark.

## BitLocker: Full Disk Encryption

BitLocker: Just do it.

Of course, BitLocker is full disk encryption so that if the bad guys get your laptop, it’s impossible for them to see what’s on it. The laptop is a few hundred to a few thousand dollars; the data on that laptop is priceless.

What’s interesting about BitLocker is that it’s configured with Intune, but it’s really Azure that does the work and where the final keys are stored.

There are a few ways to force BitLocker to be on.

### Enabling BitLocker Using Intune

There are a variety of ways to turn BitLocker on while using Intune. Well, actually, Intune does the “turning on,” but the real enforcement is through Azure (as are the BitLocker keys). More on this in a bit.

The variety of ways you could turn on BitLocker are as follows:

*   Intune’s device profiles
*   Alongside Autopilot
*   PowerShell and deploying a script

Let’s explore each of these options.

Before we do though, we need to talk about the idea of a device owner. A device owner is the person who first enrolled the device into Azure (which then gets auto-enrolled into MDM). Maybe that person to enroll the device was Frank Rizzo, your global admin, after a machine was up and running with Windows (and enrolled later). Maybe that person was Jack Tors, who enrolled the machine alongside the OOBE pages with Autopilot.

In `Azure ➢ Devices`, you can see the owner of each machine, as seen in [Figure 10.10](#c10.xhtml#figure10-10).

![Figure 10.10 Using Azure AD to see the device owner](images/c10f010.jpg)

[**Figure 10.10**](#c10.xhtml#figureanchor10-10) Using Azure AD to see the device owner

That idea of the device owner—the first person to register the device in Azure and MDM—is going to be a key thing. So keep that in the back of your brain as we continue.

#### Enabling BitLocker via Intune Device Configuration Profiles

Here’s one way to turn BitLocker on. Note that these steps require Windows 1809 or later to work as expected.

Start out by going to `Intune ➢ “Device configuration” ➢ Profiles`. Then create a new profile with type of “Endpoint protection” as seen in [Figure 10.11](#c10.xhtml#figure10-11). Then click into Windows Encryption policies.

![Figure 10.11 How to turn on BitLocker for a device](images/c10f011.jpg)

[**Figure 10.11**](#c10.xhtml#figureanchor10-11) How to turn on BitLocker for a device

Then, there’s a huge array of settings inside. The only one strictly required to make this work is seen in [Figure 10.12](#c10.xhtml#figure10-12)—namely, setting “Encrypt devices” to Required. But if that’s the only setting you select, then BitLocker will only activate and start to encrypt when a local admin is on the box, and not a standard user. To adjust for this, select Block for “Warning for other disk encryption,” which gives you the ability to select Allow for “Allow standard users to enable encryption during Azure AD Join.” That policy name itself is a little misleading, because (I tested it) it works after the machine is Azure AD joined, not necessarily during or “at the moment of” Azure AD Join as the name implies. Maybe a better name would have been “Allow standard users to enable encryption when Machine is Azure AD Joined.”

I’m also a fan of the following two settings: “Save BitLocker recovery information to Azure Active Directory” and “Store recovery information in Azure Active Directory before enabling BitLocker” (both seen in [Figure 10.13](#c10.xhtml#figure10-13)). For me, I like the idea that the keys are escrowed (or saved on the computer’s behalf). And I like the idea that encryption won’t even start until I know the keys are up there in the cloud somewhere. (More on this in a bit.) But I can also see the logic in not forcing this, at the sake of just ensuring that all machines “out there in the wild” are encrypted, even if there’s some problem getting the recovery keys stored in Azure AD.

Another pretty good idea would be to Block the “Write access to fixed data-drive not protected by BitLocker” (which is not shown).

When this is all set up, and saved, you can assign it to a group. For my example, I’ve created a group with a single test machine, but if your lab is small enough, you can also try to assign the profile to All Devices (not recommended in real life, but should be okay here).

![Figure 10.12 Enabling BitLocker encryption for the main drive and enabling standard users to encrypt the drive](images/c10f012.jpg)

[**Figure 10.12**](#c10.xhtml#figureanchor10-12) Enabling BitLocker encryption for the main drive and enabling standard users to encrypt the drive
