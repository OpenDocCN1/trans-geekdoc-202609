# Chapter 3 Types of Authentication 83

Other downsides include that TOTPs are relatively expensive versus other MFA solutions and they can become unsychronized from the server-side authentication source. Most TOTP devices are designed to tolerate some small amount of time skew, but if the device goes beyond the threshold limits, the device will stop allowing successful authenticating.

To fight the time skewing issue, some OTP devices work purely on "asynchronous" challenge-response solutions. In these scenarios, the user usually generates a "challenge," which is then input into the stand-alone OTP device, which in turn generates a related, "response." The response is sent to the server and compared to the server's self-generated response value. If they match, the client is authenticated. RFC 6287 covers asynchronous OTP devices.

> NOTE The Initiative for Open Authentication, or OAuth (en.wikipedia.org/wiki/Initiative_for_Open_Authentication), is involved with setting open standards for OTP devices. OAuth (or OAUTH) should not be confused with OAuth, which is another unrelated standard called Open Authentication, covered more in Chapter 19, "API Abuses."

OTP MFA devices are very popular, and for while they seemed to become the future MFA solution of choice, but the wide availability of cell phones being used as MFA hardware devices and software-based OTP solutions have diminished their exponential rate of growth. More on OTP solutions and how to hack them in Chapter 9, "One-Time Password Attacks."

# Physical Connection Devices

Another very popular hardware-based authentication device type is one that requires physical connections to the device it is being used to authenticate to or from.

# Dongles

Early examples of physical connection devices included devices a user had to connect to their computer's serial or parallel port to run software. In the 1980s and 90s, to prevent illegal software copying, an antitft device was a popular choice; the software had to check for the presence of this device before it ran. The device usually contained a serial number or some other code that could be queried and, if matched, the device would successfully authenticate the software and allow it to run. Related to these were illegal cable box "descramblers" or signal baluns, which allowed customers to access cable channels they had not subscribed to.

# USB Devices

In more modern times, many MFA solutions involve plugging an authentication device into the base computing computer's USB port. Nearly every computer and laptop has multiple USB ports, USB-based authentication devices have been popular for at least two decades. USB-based authentication devices may need to be plugged in to boot up a device, to unlock an encrypted hard drive, or to authenticate to participating sites and services.