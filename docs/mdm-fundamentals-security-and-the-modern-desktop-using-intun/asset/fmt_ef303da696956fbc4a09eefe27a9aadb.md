
# Microsoft 365 Business

This is for small and medium-size businesses, usually fewer than 300 seats. Organizations with this subscription can partake in the fun as well.

As I said, Autopilot is really its own service, but there’s a place inside Intune to manage it. The fastest way to get there inside Intune is **Device enrollment** ➢ **Windows Enrollment**, where you can then see a section entitled **Windows Autopilot Deployment Program**, as seen in [Figure 8.14](#c08.xhtml#figure8-14).

![Figure 8.14 The Autopilot section within Windows Intune](images/c08f014.jpg)

[**Figure 8.14**](#c08.xhtml#figureanchor8-14) The Autopilot section within Windows Intune

In the next few sections, we’ll spend time within these areas (in the following order):

*   Devices
*   Deployment profiles
*   Enrollment status page (often abbreviated ESP)
*   Intune Connector for Active Directory

You’re welcome to poke around for a second, but I recommend holding off configuring anything until we’re ready to do so.

## Manually Getting a Hardware ID into Autopilot

What we’ll do in this section is an excellent “walk before you run” with Autopilot. We’ll grab one machine’s hardware ID and put it into Autopilot.

We’ll use a PowerShell script running upon an existing, “up and running” Windows 10 machine (1703 or higher). The script outputs a CSV file that we’ll then have Autopilot consume.

Why would you want to do this with an “up and running” Windows 10 machine? Well, normally you wouldn’t. Remember, the core scenario of Autopilot is “you buy a bunch of machines from Dell or Lenovo and then ship them to your end users.”

But you’re going to need to pre-flight-test Autopilot so you know it’s working perfectly. So when you get the ID of a test system or two or three, you can then keep trying and retrying. Nuking the box, and restarting the out of box experience. Try and try again until you know you’ve got it right.

Then you’ll have it down to a science with your test machines, so that your real “bulk purchased” machines will correctly check in to Autopilot and get bootstrapped and get started with the experience I outlined earlier.

So this is going to be the best first steps and first experiences with Autopilot. But you would have to touch each machine in order to utilize this method, which is not handy…not at all. But don’t panic. In the next sections you’ll learn how to mass-gather device hardware IDs.

In this example, I’m using a machine with Windows 1809 on it that is not domain-joined, not enrolled in MDM. It just exists. And one I plan to blow away again and again, so it has nothing particularly useful on it. If you’re following along, for this chapter, I highly recommend bringing up a brand-new VM you’ve never registered into Intune before. In this way you won’t run into any problems where your hardware ID is already preassigned to some computer name in Azure and/or Intune.

Once your newly created test Windows 1809 machine is running, there’s a script we can leverage from the PowerShell gallery. You can get it the hard way directly from the PowerShell gallery at `www.powershellgallery.com/packages/Get-WindowsAutopilotInfo/`. Or, you can get it the easy way. Let’s go with the easy way.

To use it, start out by running an Admin PowerShell prompt. Then run:

```
Install-Script -name Get-WindowsAutopilotInfo
```

Say yes to any prompts (see [Figure 8.15](#c08.xhtml#figure8-15)).

![Figure 8.15 Running the Get-WindowsAutopilotInfo PowerShell script](images/c08f015.jpg)

[**Figure 8.15**](#c08.xhtml#figureanchor8-15) Running the `Get-WindowsAutopilotInfo` PowerShell script

When done, you’re almost ready to use the script. You’ll need to tell Windows it’s A-OK to run scripts. Then run the script and save the hardware ID as a CSV file someplace handy.

```
Set-ExecutionPolicy Unrestricted
Get-WindowsAutopilotInfo -outputfile c:\out1.csv
```

Then open the file with Notepad, as shown in [Figure 8.16](#c08.xhtml#figure8-16), to check it out.

![Figure 8.16 Examining an Autopilot hardware ID](images/c08f016.jpg)

[**Figure 8.16**](#c08.xhtml#figureanchor8-16) Examining an Autopilot hardware ID

Get this file over to your management station and keep it handy. In the next step, you’ll upload the CSV file into Autopilot (through the Intune console).

## Uploading Your Device CSV File into Autopilot

Back in the screen shown in [Figure 8.14](#c08.xhtml#figure8-14), look for, and then click upon the **Devices** category.

Next you’ll be able to click **Import** and then feed it your CSV file. You can see this in [Figure 8.17](#c08.xhtml#figure8-17).

![Figure 8.17 Feed Autopilot your CSV file.](images/c08f017.jpg)

[**Figure 8.17**](#c08.xhtml#figureanchor8-17) Feed Autopilot your CSV file.

In this example I’m feeding one hardware ID, but you can feed it up to 175 IDs at a time. Then sit back and wait. This process takes a while to complete.

When done it will look similar to what’s seen in [Figure 8.18](#c08.xhtml#figure8-18).

![Figure 8.18 Your device shows up as registered in Autopilot.](images/c08f018.jpg)

[**Figure 8.18**](#c08.xhtml#figureanchor8-18) Your device shows up as registered in Autopilot.

You can come back here in a bit to verify that the hardware ID is A-OK.

In the meantime, you can continue onward and make your Intune Autopilot profile. Before I forget, here are some more resources about getting the hardware ID manually:

*   `https://blogs.technet.microsoft.com/mniehaus/2017/12/12/gathering-windows-Autopilot-hardware-details-from-existing-machines/`
*   `https://docs.microsoft.com/en-us/windows/deployment/windows-Autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell`

## Windows Subscription Activation

When you buy a palate of machines from Dell or Lenovo or whomever, they might not ship you Windows 10 Enterprise. Instead, they might sell you Windows 10 Pro, which you’ll then drop-ship to your end users.

But, wait! You don’t want to use Windows 10 Pro; you want to use Windows 10 Enterprise. What are you going to do?

Windows Subscription Activation to the rescue!

You assign a Windows 10 E3 or E5 license in Azure AD to a user or a group of users. Then, when the user logs on, it immediately transforms the machine from Windows Pro to Windows Enterprise…bingo…just like that. And, yes, every time a user touches another machine, re-bingo. He would just keep transforming every Pro machine he touches to Enterprise.

Learn more about Windows Subscription Activation at `https://docs.microsoft.com/en-us/windows/deployment/windows-10-enterprise-subscription-activation`.

## Edition Upgrade and S Mode Switch

You might be familiar with Windows 10 in S Mode. We talked about this ever-so-briefly in [Chapter 1](#c01.xhtml). Windows 10 in S mode is a way you can buy a machine that will be very secure (hence, the *S*) and only trust applications downloaded and purchased via the Windows Store, and not those attempted to be installed on the machine like a Win32 app.

This is great, until you run into some showstopper where, at least on some machines, it turns out you do need to have, say, Windows 10 Pro or Enterprise instead. This can happen if your application is absent from the Windows Store, or needs a driver to drive some kind of unusual hardware. As I stated in [Chapter 1](#c01.xhtml), a one-way upgrade path is possible from Windows S to Windows Pro or Enterprise.

And, you can do this with Intune to one or more machines.

You do this with an **Edition Upgrade Profile**, as seen here.

![](images/c08uf002.jpg)

Then, you select the version (seen here) and give it a key (not shown).

![](images/c08uf003.jpg)

Finally, you can specify to **No Configuration**, **Keep in S mode**, or **Switch**.

![](images/c08uf004.jpg)

Note that the Windows S Mode switch only works for Windows 10 1809 and later.
