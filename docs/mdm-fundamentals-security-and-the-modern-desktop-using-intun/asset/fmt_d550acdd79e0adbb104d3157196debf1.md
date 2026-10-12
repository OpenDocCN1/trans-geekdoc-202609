
## Make the Autopilot Profile Assignment to an Azure AD Group

[**Figure 8.22**](#c08.xhtml#figureanchor8-22) Make the Autopilot profile assignment to an Azure AD group.

For good measure you can click “Assigned devices” and see which devices should get this profile, as seen in [Figure 8.23](#c08.xhtml#figure8-23).

![Figure 8.23 See which devices will get the Autopilot profile you created.](images/c08f023.jpg)

[**Figure 8.23**](#c08.xhtml#figureanchor8-23) See which devices will get the Autopilot profile you created.

I’m sure you’re ready to nuke a machine and get started with testing our Autopilot.

Don’t.

Don’t do it yet.

Just…don’t.

I recommend you continue onward, and I’ll tell you when to hit the “nuke button.”

## Setting Up Enrollment Options and Setting Up Branding

At this point you can dictate more of the Autopilot user experience via the enrollment options and (optionally) the Azure AD branding.

Both of these hone and craft the look and feel and user experience when users kick off the OOBE. So let’s get these out of the way before we even attempt our first Autopilot dry run.

### Setting Up Enrollment Options

In Intune you’ll want to express the look and feel of the user experience when the machine is getting all its brains downloaded from Autopilot.

To do this, click on the `Device Enrollment ➢ Windows enrollment ➢ Enrollment Status Page`.

Then click on the Default profile, which affects all users and devices. Note that you could create a new profile and be selective, but I’m not going to do that here.

In the Default profile, select Settings, as seen in [Figure 8.24](#c08.xhtml#figure8-24).

You can poke around here if you like, but for now, I would keep the defaults for your initial test flight. You can make it such that the machine waits for certain conditions to be true before releasing control to the end users to start working. Those options are seen in [Figure 8.25](#c08.xhtml#figure8-25), but again, I don’t recommend you turn them on right now.

![Figure 8.24 The default “All users and all devices” settings, which I recommend you use in the chapter](images/c08f024.jpg)

[**Figure 8.24**](#c08.xhtml#figureanchor8-24) The default “All users and all devices” settings, which I recommend you use in the chapter

![Figure 8.25 Additional enrollment options (which I don’t recommend for the chapter, but useful in real deployments)](images/c08f025.jpg)

[**Figure 8.25**](#c08.xhtml#figureanchor8-25) Additional enrollment options (which I don’t recommend for the chapter, but useful in real deployments)

Let’s take a look at some of the policies seen in [Figure 8.25](#c08.xhtml#figure8-25).

**Block device use until all apps and profiles are installed** When this item is selected, you get the remainder of the options. As expected, the entirety of all the applications and profiles must be downloaded before the machine is ready for the end user to use.

Note that any problems in downloading any applications at all could also hang up the installation.

**Allow users to reset device if installation error occurs** It might be a good idea to set this to Yes. In this way, a user can click the Reset button at the end of a failed OOBE and at least try again and maybe contact Autopilot and then the MDM service and succeed the second time.

**Allow users to use device if installation error occurs** You can get hard core and block the use of the Windows PC if any installation problems occur with this option set to No.

**Block device use until these required apps are installed if they are assigned to the user/device** This is a nifty feature you can use to guarantee that maybe one or two key applications are installed first on the machine and then control is released to the user. And then, later, in the background, the other nonessential applications are installed. This gets the user to work more quickly and defers the installation of lesser-used applications to a later time. You can learn more about this particular nuanced feature here:

`https://blogs.technet.microsoft.com/mniehaus/2018/12/06/blocking-for-app-installation-using-enrollment-status-page/`

There are some other settings here as well, but again, I suggest you use the defaults as seen in [Figure 8.24](#c08.xhtml#figure8-24).

### Azure AD Branding for Autopilot

A completely optional step, which is neither Autopilot-nor Intune-related, is to update the branding of your Azure AD. But when you’re done in this area, users utilizing Autopilot will see a visual difference from the defaults.

We call this “the warm fuzzies” in the IT business. Users really like this stuff. They know they’re on the right track after they get the machine out of the box; it’s a gentle reminder they’re going to be alright.

To get to Azure AD branding, click `Azure ➢ Azure Active Directory ➢ Company Branding`. There are really two fields you might want to populate: the square logo field and the rectangular logo field. The square one can be seen in various areas, but it’s the rectangular logo field that you pretty much must populate. Self-deploy mode actually requires the rectangular logo! The square logo should be 240×240. The rectangular logo should be 280×60. Also, you might need to tweak and tinker with your logos to reduce the size. Use a tool like Paint.Net or GIMP or Snag-It to reduce the physical size and on-disk size to get these small enough to be accepted.

In [Figure 8.26](#c08.xhtml#figure8-26), you can see I’ve added a bunch of logos, square and rectangular. If I took a little more time, I could make it perfect, but for my purposes, these are good enough and we’ll see them later.

![Figure 8.26 Configuring Azure AD branding, which you’ll see in Autopilot](images/c08f026.jpg)

[**Figure 8.26**](#c08.xhtml#figureanchor8-26) Configuring Azure AD branding, which you’ll see in Autopilot

Additionally, beyond the use of branding for Autopilot, branding has a handful of other functions. For instance, from this point onward, when people go to log on to, say, the Azure portal (like Frank Rizzo), they’ll also see these graphics to let them know they’re on the right track.

A great and detailed blog entry about which branding elements will appear in Autopilot as well as other areas of Azure can be found at:

`https://blogs.technet.microsoft.com/mniehaus/2017/12/22/windows-Autopilot-azure-ad-branding/`

## Final Preparation for Autopilot: Reset, Sysprep, or Reinstallation

At this point, you now have one hardware ID in Autopilot. You have set up an Assigned or Dynamic group and the Autopilot deployment profile. You’ve set up enrollment options and optional Azure AD branding.

Now you need to get a machine ripped down to the (almost) bare metal and start the out of box experience. There are three main ways to accomplish that goal:

*   Sysprep a machine (not recommended; but we’ll go through it anyway).
*   Reset a machine.
*   Reinstall a machine.

Let’s explore all those options here.

### Sysprep an Existing Machine

Now, you’ve likely used Sysprep before, but here are some quick notes:

*   Sysprep can now be run 99 times before the whole Windows image needs to be replaced. So if you’re using a virtualized machine (say, VMware Workstation or Hyper-V), I recommend you take a snapshot before the Sysprep. Then tell Sysprep to perform a Shutdown option. Then take another snapshot when the machine is powered down. (Then you’ll be ready to test and retest Autopilot.)
*   The Generalize flag seen in [Figure 8.27](#c08.xhtml#figure8-27) can be problematic. If you have any downloaded Windows Store apps, you have to uninstall them first before this will work.
*   If Sysprep just doesn’t want to cooperate, then don’t spend an hour on it. Just move on. As I said, there are other ways to flatten a machine.

![Figure 8.27 Using Sysprep to get back to the OOBE](images/c08f027.jpg)

[**Figure 8.27**](#c08.xhtml#figureanchor8-27) Using Sysprep to get back to the OOBE

Some quick side notes if Sysprep just doesn’t want to work for you:
