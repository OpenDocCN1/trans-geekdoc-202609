
And, additionally, we will overcome this problem when we talk about distributing new machines using Autopilot. But that’s all the way in [Chapter 8](#c08.xhtml)! But for now, it’s true: If someone enrolls the machine in this way using the out of the box experience, they become the local admin on the box.

Okay. Take a deep breath and let’s move onward.

Now, the next methods I want to show you will be for when the Windows 10 machine is already up and running, maybe having been used for some time. I’m going to teach you three things in this scenario:

*   The first thing is what *not* to teach your users. Yep, what *not* to do comes first.
*   The second thing is “all the manual clicks” a user would have to do in order to get MDM enrolled.
*   The third thing would be a little shortcut method to minimize the steps a user would have to perform.

### Restricting Users and Devices in Azure and Intune

Having anyone who just enrolls a machine with their username and password automatically become a local admin of the Windows 10 machine: crazy bad idea.

Crazy good news: You can fix this with Azure’s Device settings, in a section called device type restrictions.

First, in Azure’s portal (not in Intune), when you click Devices and then “Device settings,” there are a handful of interesting options you may want to know about. You can see them here.

![](images/c02uf002.jpg)

You can use the items on this page as follows:

*   To limit which users may join devices to Azure AD
*   To add which Azure users will also be local administrators on your AAD joined devices
*   To specify how many devices a user can have. Could be handy to set it to 1 or 2 instead of 50 or unlimited.

The second, related idea is how you can use the Intune console to prevent personally owned devices from being able to make their way into Intune. When you do this, you ensure that devices you know about are coming into Intune and not random machines purchased at Best Buy or Amazon.

Okay then, if you block personally owned devices, then what is the definition of personally owned, versus, say, corporate owned?

The web page on the subject is here: `https://docs.microsoft.com/en-us/intune/enrollment-restrictions-set#set-device-type-restrictions`, and here are the relevant characteristics:

*   The enrolling user is using an admin style account, also known as a device enrollment manager account. A nice step-by-step is found at `https://prajwaldesai.com/adding-microsoft-intune-device-enrollment-manager/`.
*   The device is enrolled through Windows Autopilot (discussed in [Chapter 8](#c08.xhtml)).
*   The device enrolls through a bulk AAD Token via a provisioning package (also discussed in [Chapter 8](#c08.xhtml)).
*   The device enrolls through automatic enrollment via SCCM for co-management.

There are some other restrictions too, but these are the big ones.

If you want to tweak Intune to block personally owned devices, which would then prevent (what should be) standard users from becoming local admins on the Windows 10 machine, then in Intune, go to Device Enrollment ➢ Enrollment Restrictions. Inside Device Type Restrictions, you can click Properties and select the “Configure platforms,” then within the “Personally Owned” column, click Block upon the type of device you want to restrict; in our case Windows 10, as seen here.

![](images/c02uf003.jpg)

### What Not to Do: Azure AD Join, but No MDM Enrollment

Why am I showing you what *not* to do first? Because, it seems like the most obvious path you (or your users) would take. Trust me, you’ll see what I mean.

These examples are using a Windows 10 1809 machine; your experience may be a little different in future versions of Windows. But this is what I’ve got to show you today.

Pretend to be a Standard User (that is, one without any local admin rights), and go to the Start bar and type in `MDM`. For me, and I swear I’m not making this up, I also got some nice recommendations about the mind-altering drug MDMA. But, erasing the recommended A in MDMA will get you what you see in [Figure 2.18](#c02.xhtml#figure2-18).

![Figure 2.18 Using Windows search to look for MDM settings ](images/c02f018.jpg)

[**Figure 2.18**](#c02.xhtml#figureanchor2-18) Using Windows search to look for MDM settings

This enables the user to click either “Enroll in MDM only” (two choices) or “Access work or school.”

Again, maybe it’s just me, but in 1809, clicking “Enroll in MDM only” (the left side or the big right-side link) actually did *nothing* at all except bring me to the Windows Settings page (yippee). (I even tried this as a local admin, and nothing occurred at all.)

Now as this pretend user, inside Windows Settings I have to type `MDM` again, where you’ll see what’s in [Figure 2.19](#c02.xhtml#figure2-19).

![Figure 2.19 Use the Settings app ](images/c02f019.jpg)

[**Figure 2.19**](#c02.xhtml#figureanchor2-19) Use the Settings app

Once again, trying “Enroll in MDM only” again from here gives me…exactly nothing again. Literally. It goes nowhere at all.

Okay. (Remember, you’re trying to think like the user, and a Standard User at that.) So let’s try “Access work or school.” Okay! That works. On that page is a big + (plus) with the word *Connect*. Great, let’s click on that.

Then the big, beautiful dialog box you’ll see next is seen in [Figure 2.20](#c02.xhtml#figure2-20), where you would expect a user to put in their Azure AD account information.

![Figure 2.20 The “Set up a work or school account” dialog box. Just waiting to eat your end users for lunch. ](images/c02f020.jpg)

[**Figure 2.20**](#c02.xhtml#figureanchor2-20) The “Set up a work or school account” dialog box. Just waiting to eat your end users for lunch.

Then, they log on with the username and password they got from email.

As it’s cooking, it will look like [Figure 2.21](#c02.xhtml#figure2-21).

![Figure 2.21 As the connection to Azure AD occurs, you’ll see something like this. ](images/c02f021.jpg)

[**Figure 2.21**](#c02.xhtml#figureanchor2-21) As the connection to Azure AD occurs, you’ll see something like this.

You’ll get an “All set” message and a chance to click Done. When you do, you’ll fall right, directly, squarely into the snake pit, like Indiana Jones does in *Raiders of the Lost Ark*.

Here’s an example of the wrong icon, seen in [Figure 2.22](#c02.xhtml#figure2-22). It looks like the Windows flag icon. This is not what you want to see if you wish to be MDM enrolled.

![Figure 2.22 The Windows icon after enrollment means you’re “Workplace joined” and not really MDM enrolled. ](images/c02f022.jpg)

[**Figure 2.22**](#c02.xhtml#figureanchor2-22) The Windows icon after enrollment means you’re “Workplace joined” and not really MDM enrolled.

How do you know you are not *actually* MDM enrolled? Only because you’re reading this book of course. Because to me, a nice Windows flag seems like a good thing. But it’s actually wrong and not enough for MDM.

But you can see for yourself if you click on the flag, click “Manage your account,” and open the page in a browser, like Edge. You’ll see in [Figure 2.23](#c02.xhtml#figure2-23) where the computer is merely *Workplace joined* and not MDM enrolled.

![Figure 2.23 You don’t want to be Workplace joined. You want to be MDM enrolled, which is explained next. ](images/c02f023.jpg)

[**Figure 2.23**](#c02.xhtml#figureanchor2-23) You *don’t* want to be Workplace joined. You want to be MDM enrolled, which is explained next.

To understand what you’ve just done, which, again, is called Workplace Join, see the sidebar “What Is Workplace Join?”

### What Is Workplace Join

If you’re not MDM enrolled in [Figure 2.22](#c02.xhtml#figure2-22), then what *have* you done there?
