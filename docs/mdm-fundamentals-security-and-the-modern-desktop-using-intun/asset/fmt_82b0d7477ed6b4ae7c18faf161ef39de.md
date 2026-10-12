
![Figure 10.13 Forcing BitLocker encryption for removable drives and storing the recovery information to Azure AD](images/c10f013.jpg)

**Figure 10.13** Forcing BitLocker encryption for removable drives and storing the recovery information to Azure AD

Then, as you might expect, sync with Intune.

What happens next?

Well then, it depends on who you *are*. More specifically who you are logged in as—a standard user or a local admin—when you get the policy.

If you are a standard user when you get the policy, a whole lot of *nothing at all appears to happen*. But in reality, underneath the hood, BitLocker encryption is kicked off and doing its thing as seen in **Figure 10.14**.

![Figure 10.14 No indication BitLocker has started for a Standard User, but the drive begins encryption](images/c10f014.jpg)

**Figure 10.14** No indication BitLocker has started for a Standard User, but the drive begins encryption

If you are an admin when you get the policy, you will get a simple pop-up notice that BitLocker encryption has started (not shown).

At this point it’s off to the races.

### Enabling BitLocker alongside Autopilot

This device owner thing is a real headache. There is a way to get out of it, but you have to think it through and deploy fresh machines to end users using Autopilot.

If you’ll remember back in **Chapter 2**, “Set Up Azure AD and MDM,” when we hand-enrolled a machine to MDM via the out of box experience, the person doing the enrollment became a local admin, which also meant they became the device owner. And likewise, also in **Chapter 2**, when we hand-enrolled a machine to MDM via “Set up a work or school account,” that person also became a local admin, and at that time they also became the device owner.

It was only when we use Autopilot that the magic worked: When the machine was done enrolling into MDM via Autopilot, the end user was just a standard user on the box, and…*they* became the device owner.

So, when possible, using Autopilot to do your rollouts has a big advantage when you also roll out BitLocker at the same time. The end user on the box becomes the owner, and they can see their own BitLocker recovery keys in their portal information page (more on this in a bit in the “BitLocker Key Recovery and Management” section).

Now, there are two types of BitLocker-capable devices in the world:

*   Hardware Security Test Interface (HSTI) and/or InstantGo capable
*   Non-HSTI/Non-InstantGo capable

Newer hardware is HTSI/InstantGo; older hardware and virtual machines are Non-HSTI/InstantGo.

Depending on your target machine, you have to set up BitLocker settings a little differently.

Note that if you followed along in the Autopilot chapter (**Chapter 8**, “Rollouts and Refreshes with Configuration Designer and Autopilot”), then you might have various Autopilot Deployment profiles. I recommend for now to un-assign all profiles except the All Devices profile before continuing, which will perform the basic user-driven experience. That way you won’t get into any hot water with conflicting Autopilot profiles or unusual or complex Autopilot scenarios. Remember also that this should work with virtual machines, if the virtual machine has a virtual TPM 2.0 chip.

![](images/c10uf002.jpg)

#### BitLocker for Non-HTSI/Non-InstantGo Capable

This scenario is pretty simple.

Just assign BitLocker test profile you created earlier to your Autopilot (All) group.

The BitLocker test profile is set to turn on disk encryption as soon as it can and escrow the keys.

Because the person enrolling the machine for the first time in Autopilot will be a standard user like Jack Tors…bingo. Jack logs on with Autopilot, he enrolls the machine to Azure AD and Intune MDM, and BitLocker encrypts the machine.

Jack becomes the device owner, and all is right in the world.

A quick side note if you’re testing this with VMware Workstation and are using a vTPM 2.0 chip and aren’t on real hardware. For me, Autopilot wouldn’t kick in unless the vTPM chip was removed, then re-added. Specifically, I was able to add the vTPM chip after Autopilot discovered the machine and rebooted it after the rename. At that point I shut down the virtual machine and added in the vTPM chip. Only then would Autopilot be bootstrapped, see the machine, see the vTPM, and continue onward without incident.

Again, you shouldn’t need to do any of those gyrations in the real world with real TPM hardware. And maybe it “just works” for you with VMware Workstation as well and I just experienced something weird that moment.

#### BitLocker for HTSI/InstantGo Capable

These kinds of machines will automatically begin to perform BitLocker encryption as soon as they are joined to Azure AD. Wow.

If you want some details on InstantGo and the automatic BitLocker-ing when joining Azure AD, check out:

`https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2016/03/14/automatic-BitLocker-on-windows-10-during-azure-ad-join/`

Here’s the key takeaway though; it’s weird, so stick with me. Ironically, your Windows Encryption settings in the Intune profile need to be set to “Not configured” for “Encrypt devices,” as seen in **Figure 10.15**.

There are two blog articles that gave me the formula here:

`https://osddeployment.dk/2018/11/18/how-to-delivering-BitLocker-policy-to- Autopilot-devices-to-set-256-bit-encryption/`

`https://techcommunity.microsoft.com/t5/Microsoft-Intune/BitLocker-Encryption-Policy-for-Autopilot-Devices-Windows-10/td-p/291187`

Let me break it down though a lens based upon what you’ve already set up in the book:

*   Do *not* recycle the device profile with BitLocker settings you created earlier. Instead, create a brand-new Windows 10 device profile with “Endpoint protection” policy settings. (The MVPs from the blog have reported that the settings will not work if applied when using an existing profile! But I didn’t try that.)
*   In the “Windows Encryption” settings pane, this is weird: Leave the “Encrypt devices” setting to “Not configured.” This is a critical step! See this in **Figure 10.15**.
*   Do select “Warning for other disk encryption” to Block and “Allow standard users to enable encryption during Azure AD Join” to Allow.
*   Do other settings on the page that you wish.
*   Create a new Azure AD group for Autopilot or use an old one. I’m going to assign my new BitLocker with Autopilot profile to my Autopilot (All) group from **Chapter 8**, “Rollouts and Refreshes with Configuration Designer and Autopilot,” which will hit every Autopilot device.
*   Make sure that the Windows 10 ESP (Enrollment Status Page) is enabled for all Autopilot devices. This is the default as we set it up (and you can see an example of the Windows 10 EST seen way back in Figure 8.31 if you want to double-check what I mean.

![Figure 10.15 For hardware with HTSI/InstantGo, do not select to perform encryption; that happens automatically.](images/c10f015.jpg)

**Figure 10.15** For hardware with HTSI/InstantGo, do not select to perform encryption; that happens automatically.

Now, get reset or otherwise get an “already registered machine in Autopilot” to kick off and start the OOBE process.

### Enabling BitLocker via PowerShell Script

There is an alternate method to enabling BitLocker, which I did not try out but looks promising. And, this method also works if for some reason you are using a version of Windows 10 earlier than 1809. There is a jankier method to kick off BitLocker when only a standard user is available.

Basically, you use the PowerShell scripting method to twiddle BitLocker as SYSTEM, and the user is none the wiser.

I wouldn’t recommend doing it this way unless you absolutely had to, but the details and script to do it are here.
