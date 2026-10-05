# Chapter 3 Types of Authentication 91

![](bbox=[0.093, 0.105, 0.501, 0.273])

**Figure 3.16:** The Google Authenticator application displays OTP without any additional authentication needed.

The Bank of America app requires a login name and password each time it starts, or a biometric fingerprint (if it has been enabled). Google Authenticator, a software-based TOTP solution, requires that the user get a QR (Quick Response) code (see Figure 3.17 for an example) from each participating corporate account, website, or service. Once the Google Authenticator app is enabled on a cell phone, it can be started and restarted to get new TOTP codes without the user being prompted to authenticate again.

![](bbox=[0.093, 0.516, 0.316, 0.696])

**Figure 3.17:** Example QR code

Phone apps are very convenient. It seems everyone not only has a cell phone, but is also carrying it or near them at all times. Phone apps, in general, are fairly secure MFA options. They are tied to a person's cell phone and must be installed and authenticated to at least once. If the user's phone is automatically locked by a preset number of minutes of inactivity, the user has to authenticate to the phone before they can access the application. Even if an attacker is successful in stealing the user's cell phone number, the application doesn't automatically move to the attacker's phone using the phone number, and if the attacker tried to install and use the authentication app, they would have to authenticate at least once as the legitimate user.