
The second function of schemes is to allow the browser to initiate different local behavior. This sometimes includes the opening of a new application. The mailto: scheme is an example of this. If an anchor tag in an HTML web page includes a mailto: link, when clicked, the browser will often open an external application to send an e-mail.

## Abusing iOS

When a browser uses a particular scheme to perform an action in another application, it may provide you with additional attack vectors. This is highlighted by research published by Nitesh Dhanjani in 2010 on the insecure handling of URI schemes within Apple’s iOS.23

Dhanjani’s research investigated native iOS protocol handling routines, such as the tel: handler. If the iOS Safari browser requested a URL, such as tel:613-966-94916, the phone application would initiate and prompt the user to begin dialing the proposed number, as shown in [Figure 6-23](#c06.html#figure6-23).

 start figure 

[**Figure 6-23:**](#c06.html#figureanchor6-23) iOS handling the tel: scheme

![c06f023.tif](image_fi/662090c06/c06f023.png)

 end figure 

This example alone does not necessarily indicate an insecure implementation, because the phone application still prompts the user to confirm the call before proceeding. You could get lucky and the target could accidently press the call option. This is very unlikely though, so let’s take a look at another example.

Skype doesn’t come bundled with iOS but it does use its very own scheme. To allow other applications to take advantage of custom URI schemes, Apple includes a CFBundleURLTypes array type in its Info.plist specification.24 This can be seen in the following snippet from the Info.plist file:

```
<key>CFBundleURLTypes</key>
  <array>
    <dict>
      <key>CFBundleURLName</key>
        <string>com.skype.skype</string>
      <key>CFBundleURLSchemes</key>
        <array>
          <string>skype</string>
        </array>
    </dict>
  </array>
```

Skype not only exposed this scheme to the browser, but it also accepted additional parameters. For instance, if the URL was appended with ?call, not only would Skype start, but it would immediately attempt to call the number without user intervention. All the browser needed to do was load a URL similar to [skype://613-966-94916?call](http://skype://613-966-94916?call) and Skype would be spawned in the foreground of the iOS device. To take advantage of this feature it was easy enough for any web page to include an IFrame with these particular URLs. You can see a demonstration of this exploit in a video at [https://browserhacker.com](https://browserhacker.com).

Skype addressed this issue as of version 3.0, and now prompts the users if they want to proceed with the action, as shown in [Figure 6-24](#c06.html#figure6-24).

 start figure 

[**Figure 6-24:**](#c06.html#figureanchor6-24) iOS attempting to dial a number within Skype

![c06f024.tif](image_fi/662090c06/c06f024.png)

 end figure 

Dhanjani’s research explores a couple of methods in which to analyze Info.plist files, including simply copying them from a jailbroken iOS device, or extracting them from application backups through iTunes. To extract the Info.plist file from an application’s files within iTunes’ backup, perform the following steps:

Level1 **1.** Locate the .ipa file you want to investigate. Under OS X they are usually located in ~/Music/iTunes/iTunes Media/Mobile Applications. In Windows they’re usually found under C:\\Users\\<user>\\My Music\\iTunes\\iTunes Media\\Mobile Applications\\. **2.** Copy the <application>.ipa file somewhere else, and rename it to a .zip file. **3.** Unzip the file. **4.** Change into the Payload/<application>.app/ folder. **5.** Convert the Info.plist file into XML by using the plutil utility. For example, plutil -convert xml1 Info.plist. Under Windows, plutil.exe is located in C:\\Program Files\\Common Files\\Apple\\Apple Application Support\\. 

/Level1

There’s a whole raft of iOS applications out there, many of which may be introducing unusual URI scheme handling routines. Armed with this Info.plist interrogation technique, you can discover what other schemes your iOS browser might be using. There may be vulnerable flaws similar to Skype’s initial insecure handling of the skype:// scheme.

## Abusing the Samsung Galaxy

The Unstructured Supplementary Service Data (USSD) protocol provides a method for GSM cellular phones to communicate directly with the user’s telecommunications provider. The service is often found on prepaid mobile phone plans as a method to find out your remaining balance, or to even top up the credit available on your phone. Of course, USSD has other uses, such as mobile banking, or even updating Twitter or Facebook.

Although many of the USSD codes can initiate a real-time connection back to the telecommunications provider, some of these have particular actions assigned to them within the phone handset itself. For example, in most smartphones if you open the telephone application and enter \*#06#, often without even hitting the dial button, your International Mobile Station Equipment Identity, or IMEI, is displayed. [Figure 6-25](#c06.html#figure6-25) shows the IMEI on an Android phone, and [Figure 6-26](#c06.html#figure6-26) demonstrates the same function on an iPhone.

 start figure 

[**Figure 6-25:**](#c06.html#figureanchor6-25) Android IMEI

![c06f025.tif](image_fi/662090c06/c06f025.png)

 end figure   start figure 

[**Figure 6-26:**](#c06.html#figureanchor6-26) iPhone IMEI

![c06f026.tif](image_fi/662090c06/c06f026.png)

 end figure 

Ravishankar Borgaonkar released research demonstrating that some Android phones would execute USSD codes without any user interaction.25 The vulnerability existed in the way in which Android phones would process the tel:// URI scheme. The attack was very similar to the vulnerabilities in iOS discovered by Dhanjani. However, instead of activating the phone application and asking to dial a number, Android phones would immediately perform the USSD action.

Borgaonkar’s research proceeded to uncover multiple ways in which an Android phone may receive the USSD code, and subsequently execute it. Many of these relied on the default behavior of associated applications. Often the application would detect the presence of the tel:// URI scheme and simply hand the information over. This included:

*   Embedding a malicious IFrame in a website that directed the Android phone to a specific tel:// USSD code.

*   Embedding a tel:// USSD address in a QR code.

*   Embedding a tel:// USSD address in an NFC tag.

Looking at the previously discussed USSD code of \*#06#, the impact of this issue may be seen as negligible. What does it matter if you can cause an IMEI code to display on the target’s phone? The problem is that one of the issues highlighted by Borgaonkar was that some USSD codes could be used to attempt to enter the SIM code.

In many instances, if the incorrect SIM code is entered three times, the SIM is locked until a PIN Unlocked Key (PUK) code is entered. Building on this attack, an invalid PUK could then be entered 10 times, which leads to the SIM card itself being invalidated and therefore unusable. Exploiting this would mean that the target would have to get a new SIM card, often at their own expense, and their phone would be rendered useless until a new SIM card was installed.

Borgaonkar also demonstrated another USSD code that impacted particular Samsung phones that would initiate a factory reset of the device. A list of USSD codes is maintained on the XDA Developers forum here: [http://forum.xda-developers.com/showthread.php?t=1953506](http://forum.xda-developers.com/showthread.php?t=1953506)
