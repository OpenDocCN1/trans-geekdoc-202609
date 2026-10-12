
# Note on ADMX File Settings

Note that not every ADMX file will nicely have the same setting on both the user and the computer side, but this one from Foxit Reader does.

Now, you can add your second policy into the profile. To do this, click **Add** in the OMA-URI settings blade, then when **Add Row** appears, you can add the policy to disable Foxit Updater.

You’ll put in the Name, user, or device OMA-URI you created 10 seconds ago (I’ll use device in my example), give it data type of String, and then for Value, type in `<enabled/>` with no spaces. You can see the policy in [Figure 3.30](#c03.xhtml#figure3-30) (left) if you wanted to deliver the setting on the computer side and [Figure 3.30](#c03.xhtml#figure3-30) (right) if you wanted to deliver the setting on the User side.

![Figure 3.30 Add the value to disable Foxit Updater. You can deliver the value to Device (left) or User (right).](images/c03f030a.jpg)

[**Figure 3.30**](#c03.xhtml#figureanchor3-30) Add the value to disable Foxit Updater. You can deliver the value to Device (left) or User (right).

Click **Save** to save the value, then again to save the profile. Then assign it to **All Devices**. Note that you must assign the profile to Devices, even if you want the settings to affect the User side. Weird, right? It’s because the URI of the ADMX setting itself (`./User` or `./Device`) does the magic after the setting is delivered to the device side.

Back on your Windows 10 machine, if Foxit Reader is still open, close it. Then sync with the MDM service. You should see what you see in [Figure 3.31](#c03.xhtml#figure3-31), showing your custom ADMX ingested settings.

![Figure 3.31 You can see the ingested custom ADMX policies in the MDM sync (after you close and reopen the page).](images/c03f031.jpg)

[**Figure 3.31**](#c03.xhtml#figureanchor3-31) You can see the ingested custom ADMX policies in the MDM sync (after you close and reopen the page).

Then open Foxit Reader and go to **File** ➢ **Preferences** ➢ **Updater**.

You should see the UI for Foxit Reader locked out and not configurable by the user as seen in [Figure 3.32](#c03.xhtml#figure3-32).

![Figure 3.32 Successful lockout of Foxit reader with ingested ADMX file](images/c03f032.jpg)

[**Figure 3.32**](#c03.xhtml#figureanchor3-32) Successful lockout of Foxit reader with ingested ADMX file

And you can check a few locations to see if your settings are being written to the Registry (and note these are good troubleshooting steps too).

Remember that the ADMX definitions themselves are basically delivered to the client and then stored locally. Where is this? In `HKLM\Software\Microsoft\PolicyManager\AdmxDefault\{GUID}` as you can see in [Figure 3.33](#c03.xhtml#figure3-33). You should see the entire Foxit Reader ADMX we sent down.

![Figure 3.33 The entire ADMX downloaded into the Registry](images/c03f033.jpg)

[**Figure 3.33**](#c03.xhtml#figureanchor3-33) The entire ADMX downloaded into the Registry

Then, the actual thing we want to verify, the Group Policy location of the write, can be seen in [Figure 3.34](#c03.xhtml#figure3-34). You’re going for `HKLM\Software\Policies\Foxit\Reader 9.0\Preferences` and see that DisableUpdate is set to 0 (which is a little unusual; most well-written ADMX files would usually be something like DisableUpdate set to 1, but, I can roll with it).

![Figure 3.34 The Group Policy location is written to by the ADMX.](images/c03f034.jpg)

[**Figure 3.34**](#c03.xhtml#figureanchor3-34) The Group Policy location is written to by the ADMX.

![image](images/tip.jpg) If this seems like an insane amount of work, well, you’re right, it is. Again, at least Intune will likely have some kind of ADMX “ingesting” routine for third-party ADMX settings. But also note that PolicyPak MDM can do this as well, for just about every application, and lock those settings down (even for many applications that don’t have built-in lockdown). This is with our PolicyPak Application Manager component within PolicyPak MDM. And those lockdown settings for applications can be deployed using Group Policy or your MDM service. Check out `www.policypak.com/products/policypak-application-manager-including-policypak-designstudio.html` for some demo videos that greatly reduce the frustration in this process.

You can learn more about ingesting ADMX files into an MDM service with the following URLs:

*   `https://docs.microsoft.com/en-us/windows/client-management/mdm/understanding-admx-backed-policies` (search for the word Ingest)
*   `https://docs.microsoft.com/en-us/windows/client-management/mdm/win32-and-centennial-app-policy-configuration`
*   `https://www.petervanderwoude.nl/post/deep-dive-ingesting-third-party-admx-files/`

## Replacing Existing ADMX Settings on the Endpoint

Okay, let’s jump ahead into the future a little bit.

You’ve deployed Foxit Reader 9.2 and used the ADMX setting that came out with it.

Then you use your MDM service to roll out Foxit Reader 9.3, and it has some features in it that can be controlled by ADMX. Maybe Foxit Reader 9.3 has a new setting (and I’m making it up here), Theme Colors.

“Nifty!” You think to yourself, “I’ll just update and overwrite the ADMX definitions I’ve already placed into the profile (back in [Figure 3.28](#c03.xhtml#figure3-28))! And when I paste in the updated ADMX settings, I’ll simply get the ability to now manage the nifty new Theme Colors policy setting that Foxit Reader 9.3 has to offer!”

Bam. Right into the snake pits!

I wouldn’t have guessed this behavior either, but apparently the MDM engine cannot handle this situation.

When you attempt to wholesale-replace the ADMX definitions for the custom application, it simply doesn’t work.

Chasing this down, I found a very “fine print” kind of reasoning in the PolicyCSP docs:

`https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-configuration-service-provider`

Here’s the quote:

> Policy/ConfigOperations/ADMXInstall/AppName/Preference/UniqueID Added in Windows 10, version 1703. Specifies the unique ID of the app ADMX file that contains the preference to import. Supported operations are Add and Get. Does not support Delete.

Do you see the problem? “Does not support Delete.”

So you’ve upgraded (really, replaced) the ADMX definitions with newer ones. And the MDM engine sees the change and says, “Can’t help ya, man.”

The result (at least) is an error in the Microsoft ➢ Windows ➢ DeviceManagement-Enterprise-Diagnostics-Provider logs like what’s seen here in Event 454.

![](images/c03uf003.jpg)

Because the existing ADMX definitions cannot be deleted, they cannot be replaced. So the engine kind of goes into a stalemate, and you don’t get your updates.

Note this story is not limited to Foxit Reader; it could be referring to the idea of upgrading Office 2016 ADMX with a slightly newer one or Firefox ADMX with a slightly newer one, etc.

So how do you get out of this jam? There are three answers as I see it today:

*   **Choice 1:** Create a new profile expressly for the newer application.
*   **Choice 2:** Pre-run some kind of custom cleanup PowerShell script to scrape the data out of the Registry manually. Your goal would be to remove the `HKLM\Software\Microsoft\PolicyManager\AdmxDefault\{GUID}` data that stores the ADMX contents.
*   **Choice 3:** Use PolicyPak MDM to deliver the setting using PolicyPak Admin Templates Manager, PolicyPak Preferences Manager, or PolicyPak Application Manager (depending on the situation). When the value is needing to change, *PolicyPak just changes it*.

Maybe this just gets fixed in some later version of Windows. Maybe it gets resolved by the time you read this…or maybe not. But I wanted to make sure you did know about it if it’s “one of those things” that doesn’t get a quick fix.

## Creating and Using Groups

So far in the book, we’ve made some test profiles and then linked them either to All Users or All Computers, the two default groups that exist in Intune.
