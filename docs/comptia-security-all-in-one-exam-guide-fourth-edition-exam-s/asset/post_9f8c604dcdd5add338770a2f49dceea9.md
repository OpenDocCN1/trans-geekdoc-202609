
8. Which of the following correctly describes cross-site request forgery (XSRF)?

A. Attacking a system by sending malicious input and relying upon the parsers and execution elements to perform the requested actions

B. An enhanced data cryptographic encapsulation method

C. Attacking a system by sending script commands and relying upon the parsers and execution elements to perform the requested actions

D. Attempting to break a cryptographic system

9. Error and exception handling should be performed in what fashion?

A. All errors/exceptions should be trapped and handled in the main program.

B. All errors/exceptions should be trapped and handled in the generating routine.

C. Errors and exceptions should only be handled if they exceed a given severity.

D. Errors and exceptions should be logged; handling is optional.

10. The best process to use for determining unexpected input validation problems is ________.

11. The ________ defines the proper configuration settings for an application.

12. The two elements of application hardening are __________ and __________.

13. Explain to your coworker the key difference between cross-site request forgery (XSRF) and cross-site scripting (XSS).

14. Input validation is especially well suited for the following vulnerabilities:

__________, __________, and __________.

15. Your boss has asked you to identify two of the most dangerous software errors that your company should address as soon as possible. State where you can find the latest top 25 list of the most dangerous software errors and explain to your boss how you can address two of those top 25.

## Answers

1. C. Fuzzing is the systematic application of malformed inputs to test how the program responds.

2. A. SQL injection is modifying a database query statement through false input to a function.

3. A. Cross-site scripting (XSS) is one of the most common web attack methodologies.

4. C. Website defacement is not normally performed via cross-site scripting attacks.

5. B. The client is not a suitable place to perform any critical value checks or security checks.

6. D. One way to defend against buffer overflow errors is to treat all input from outside a function as hostile.

7. D. Cross-site scripting (XSS) exploits the trust a user has for the site.

8. A. Cross-site request forgery (XSRF) is attacking a system by sending malicious input and relying upon the parsers and execution elements to perform the requested actions.

9. B. All errors/exceptions should be trapped and handled in the generating routine.

10. fuzzing

11. application configuration baseline

12. removing unneeded services/options; securing the remaining configuration

13. Cross-site request forgery (XSRF) exploits the trust a site has in the user’s browser, while cross-site scripting (XSS) exploits the trust a user has for the site.

14. The answer should include any three of buffer overflow, reliance on untrusted inputs in a security decision, cross-site scripting (XSS), cross-site request forgery (XSRF), path traversal, and incorrect calculation of buffer size.

15. The Top 25 is maintained by MITRE, and is found at http://cwe.mitre.org/top25/.

## Mobile Device Security

In this chapter, you will

- Explore mobile security concepts
- Learn about mobile technologies
- Examine risk associated with mobile devices
- Examine risk associated with cloud environments

There has been an amazing convergence of business and individual usage of mobile devices. The convergence of cloud storage capabilities and Software as a Service (SaaS) is dramatically changing the landscape of mobile device usage. The ubiquitous presence of mobile devices and the need for continuous data access across multiple platforms have led to significant changes in the way mobile devices are being used for personal and business purposes. In the past, companies provided mobile devices to their employees for primarily business usage, but they were available for personal usage. With continuously emerging devices and constantly changing technologies, many companies are allowing employees to bring their own devices (BYOD: bring your own device) for both personal and business usage.

## Device Security

Security principles similar to those applicable to laptop computers must be followed when using mobile devices such as smartphones and tablet computing devices. Data must be protected, devices must be properly configured, and good user habits must be encouraged. This chapter will review a large number of topics specific to mobile devices. You’ll likely find that the security principles you’ve already learned apply and just need to be adapted to mobile technologies. This is one of the fastest-changing areas of computer security because mobile technology is likely the fastest-changing technology.

## Full Device Encryption

Just as laptop computers should be protected with whole disk encryption to protect the laptop in case of loss or theft, you may need to consider encryption for mobile devices used by your company’s employees. Mobile devices are much more likely to be lost or stolen, so you should consider encrypting data on your devices. More and more, mobile devices are used when accessing and storing business-critical data or other sensitive information. Protecting the information on mobile devices is becoming a business imperative. This is an emerging technology, so you'll need to complete some rigorous market analysis to determine what commercial product meets your needs.

## Remote Wiping

Today's mobile devices are almost innumerable and are very susceptible to loss and theft. Further, it is unlikely that a lost or stolen device will be recovered, thus making even encrypted data stored on a device more vulnerable to decryption. If the thief can have your device for a long time, he can take all the time he wants to try to decrypt your data. Therefore, many companies prefer to just remotely wipe a lost or stolen device. Wiping a mobile device typically removes data stored on the device and resets the device to factory settings. There is a dilemma in the use of BYOD devices that store both personal and enterprise data. Wiping the device usually removes all data, both personal and enterprise. Therefore, if corporate policy requires wiping a lost device, that may mean the device's user loses personal photos and data. The software controls for separate data containers, one for business and one for personal, have been proposed but are not a mainstream option yet.

## Lockout

A user likely will discover in a relatively short time that they've lost their device, so a quick way to protect their device is to remotely lock the device as soon as they recognize it has been lost or stolen. Several products are available on the market today to help enterprises manage their devices. Remote lockout is usually the first step taken in securing a mobile device.

## Screen-locks

Most corporate policies regarding mobile devices require the use of the mobile device's screen-locking capability. This usually consists of entering a passcode or PIN to unlock the device. It is highly recommended that screen-locks be enforced for all mobile devices. Your policy regarding the quality of the passcode should be consistent with your corporate password policy. However, many companies merely enforce the use of screen-locking. Thus, users tend to use convenient or easy-to-remember passcodes. Some devices allow complex passcodes. As shown in Figure 18-1, the device screen on the left supports only a simple iOS passcode, limited to four numbers, while the device screen on the right supports a passcode of indeterminate length and can contain alphanumeric characters.

Some more advanced forms of screen-locks work in conjunction with device wiping. If the passcode is entered incorrectly a specified number of times, the device is automatically wiped. This is one of the security features of BlackBerry that has traditionally made it of interest to security-conscious users. Apple has made this an option on newer iOS devices. Apple also allows remote locking of a device from the user's iCloud account.
