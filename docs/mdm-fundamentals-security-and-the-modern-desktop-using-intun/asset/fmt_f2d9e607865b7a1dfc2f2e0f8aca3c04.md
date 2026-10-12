
## Policy CSP

Arguably the most exercise your MDM service will have with Windows 10 will be pushing down policies that exist in the Policy CSP. Indeed, you can see an abbreviated list of some of the categories in the Policy CSP in [Figure 3.10](#c03.xhtml#figure3-10), starting with Autoplay, then Bitlocker, BITS, Bluetooth, and so on.

Again, the Policy CSP is simply one of the many CSPs that the MDM engine can take directives from. But it’s the one most closely aligned with the common items you might do in Group Policy-land and the one that has the most Windows 10 configuration items.

Some MDM systems have a way to search through or filter the settings and find the setting(s) you want to deploy. Others don’t. So for me, I like to start my investigation of interesting settings in the Policy CSP documentation here and look for the task I want to perform: `https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-configuration-service-provider`.

For instance, maybe the boss walks into your office and says, “Cortana? Bah!” Then it would be up to you to be a murderer and kill Cortana.

Okay, you’ve agreed to kill Cortana. Now how do you do that?

Start by going to the Policy CSP docs and look for items with Cortana in the name. There’s going to be a handful of them on the page. As of this writing there are these:

*   `PolicyCSP/AboveLock/AllowCortanaAboveLock`
*   `PolicyCSP/Experience/AllowCortana`
*   `PolicyCSP/Search/AllowCortanaInAAD`

Clearly, the one you want is `PolicyCSP/Experience/AllowCortana`. Click on that one to see if it’s going to fit the bill. Once you’ve isolated a setting that seems plausible, ask yourself:

*   Does it work on the Windows 10 edition I have? Pro, Business, or Enterprise?
*   Does the setting I’ve selected work with the Windows 10 version I have (1703, 1709, something later)?
*   Is this setting meant for Users or Devices?
*   Once I make this configuration change, what would I expect to see happen (or not happen)?

You can see the answers to each of these questions in [Figure 3.11](#c03.xhtml#figure3-11) for `PolicyCSP/Experience/AllowCortana`:

*   Yes, it works on all versions of Windows 10 I might have in my company (so, no Windows 10 Home support).
*   The setting is Device only (that’s important to know for scoping purposes).
*   Once this setting is set, Cortana is killed, but search keeps working. Okay, good to know.

![Figure 3.11 Getting to know a setting before deploying and testing it](images/c03f011.jpg)

**Figure 3.11** Getting to know a setting before deploying and testing it

Let’s kill Cortana now.

Back in Intune, click Device configuration, then Profiles and Create Profile. Then provide a name, like Kill Cortana. In the Platform drop-down, select Windows 10 and later. In the “Profile type” drop-down, select “Device restrictions.” Then in the “Device restrictions” section, click on General, and locate the Cortana policy.

You can see that Cortana’s policy is “Not configured” by default, which means that it must be enabled by default.

Now, let’s select Block.

All of this can be seen in [Figure 3.12](#c03.xhtml#figure3-12). Then, assign to All Devices (not shown). And, remember, if you assign this profile to Users, this isn’t going to work because the Kill Cortana setting is Device only.

![Figure 3.12 Using Microsoft Intune to block Cortana](images/c03f012.jpg)

**Figure 3.12** Using Microsoft Intune to block Cortana

Back at the endpoint, in the MDM section click on Sync last seen in [Figure 3.3](#c03.xhtml#figure3-3). You should see the time jump to now, and if all went well Cortana should disabled. That said, after syncing, sometimes it takes a while, and also sometimes it takes more than one sync.

But you’ll know it’s done after you investigate the Registry on the Windows 10 machine. In [Figure 3.13](#c03.xhtml#figure3-13), you can see `AllowCortana` is set to 0 after traversing to `HKEY_LOCAL_MACHINE\Software\Microsoft\PolicyManager\current\device\Experience`.

![Figure 3.13 See MDM setting AllowCortana in the PolicyManager section of the Registry.](images/c03f013.jpg)

**Figure 3.13** See MDM setting AllowCortana in the PolicyManager section of the Registry.

If you then remove the profile, and resync, you would get what’s seen in [Figure 3.14](#c03.xhtml#figure3-14), where `AllowCortana` is then reverted, and set back to 1.

![Figure 3.14 When the MDM profile is removed AllowCortana returns to 1 (Enabled).](images/c03f014.jpg)

**Figure 3.14** When the MDM profile is removed AllowCortana returns to 1 (Enabled).

You might not see Cortana pop back to life until you log off and back on.

### ADMX-Backed Policies

So in the previous section, we found a policy setting in the documentation, then happened to also find it as something we could graphically click on in the MDM user interface. And poof: It worked.

But not every MDM provider is the same, and not every MDM provider will GUI-enable every interesting policy setting. And sometimes new settings will only be available for testing when some future version of Windows makes an appearance. (Note: Future versions of Windows can be downloaded through the Windows Insider program.) And if you want to see those yet-to-be-born MDM settings take effect, you’ll be testing with settings that the MDM providers definitely won’t have placed into their GUIs yet.

As such, there’s a little “backdoor” way to configure a gaggle of Policy CSP settings that might not be GUI-enabled (yet). I say yet because it’s only a matter of time, usually, between when an MDM policy is shipped into Windows 10 and the MDM service then gets the memo and makes a GUI-enabled version of that policy setting. As I mentioned before, these GUI-enabled settings are sometimes called, “First Class” settings.

Or maybe the MDM provider never gets the memo and never GUI-enables the policy setting, and you’ll be glad you know about this technique to deliver these settings. These settings, again, are therefore called “Third Class” settings.

You likely wouldn’t want to use this backdoor method unless you actually need to. If it’s possible to set settings using the GUI, you should strive for that. Not only is it easier to do, but ultimately reporting on the settings is easier as well.

The settings we’ll be dealing with in this section are called ADMX-backed policies. There are only a handful (but a nice-sized handful) of these ADMX-backed policy settings. I call these “curated ADMX” settings.

The list of the curated ADMX settings can be found here:

`https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies`

As of this second, as I write this, the documentation shows that there are 386 special, curated ADMX-backed policy settings. Again, I call them curated because that’s what they are. They are special, and hand-picked by the MDM team as something they want to support and they have guaranteed results. So the complete list of ADMX-backed policy settings is at the URL above, but as you might remember from [Chapter 1](#c01.xhtml), there are over 4000 ADMX settings that Microsoft ships with Group Policy and its ADMX files.

But wait, “That doesn’t make sense” I hear you say. “If there are 4000+ ADMX settings, can’t I just do this same magic trick on *any* ADMX setting?”

No.
