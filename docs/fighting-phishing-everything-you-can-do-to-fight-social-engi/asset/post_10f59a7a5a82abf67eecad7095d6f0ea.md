
![](img/49fb1c0c9ac2e62e5db4a36fa9f8b591_247_0.png)

FIGURE 9-3 An example of a browser notification instance asking for permission to send browser notifications.

Each site or app wanting to send notification messages to a user must first ask permission, in what is known as the notification request message (which is what is shown in Figure 9-3). If the user clicks on “Allow,” that site or application can send notification messages to the user (outside of the site or application) whenever they want. If the user clicks on “Cancel” instead, the site or application will not be able to send notification messages and cannot ask again. If the user just hits escape and/or doesn’t make a selection, the site or application can ask again the next time the user visits the site or application.

If approved, browser and operating system notification messages can end up being used maliciously to send phishing messages. Every user should block browser and operating system notification messages when possible (unless you want to see them and can manage to pick out which ones are legitimate and which ones may be phishing attacks). Browsers and operating systems that support the notification standard allow users (and admins) to block or allow all notification messages by default, or to allow or block notification messages from particular sites and applications. Figure 9-4 shows an example of notification settings in Microsoft Edge.

Each browser and operating system that support notification messages have their settings in a different place, but in Microsoft Edge, they are under Settings, in Cookies and site permissions. As you can see in Figure 9-4, some specific sites have been intentionally blocked and one application, Facebook Messenger, is specifically allowed. Users and administrators can manually select the settings or use automation (such as scripting or Active Directory Group Policy) to set them across a range of users. In general, blocking notification messages reduces phishing risk.

![](img/49fb1c0c9ac2e62e5db4a36fa9f8b591_248_0.png)

FIGURE 9-4 Settings area where browser notifications can be allowed or blocked in Microsoft Edge.

To watch my one-hour webinar on malicious notification messages see: https://info.knowbe4.com/malicious-browser-notifications.

## Email Client Settings

Like browsers, most email clients have the appropriate default security settings to prevent some common forms of social engineering and phishing. Most users should make sure not to weaken the default settings to a state where it's easier for social engineering and phishing attacks. When in doubt as to whether your email client’s security settings have been overly weakened, most email clients have a “reset” settings option that allows you to quickly reset the email client back to its default behavior.

One of the most commonly misunderstood email security settings has to do with how an email client treats pictures and other content when arriving in an email. By default, most email clients will not allow active content, such as pictures, scripts, and objects to be automatically downloaded and activated when the email is first received. This is a great security protection! Don’t change it.

Most phishers and malware spreaders are hoping that users will open their emails and activate whatever content they contain. Even a simple, otherwise non-malicious, picture can be used maliciously to track the recipient and confirm their email address (known as _web beacons_). Allowing all content to be automatically downloaded and executed is a super high-risk activity. Because of this, all users (and admins) need to make sure their email clients do not automatically download and run non-text content contained in received emails. The location of this setting varies by email client, although Figure 9-5 shows an example of the relevant email security setting as it is covered in Microsoft Outlook.

![](img/49fb1c0c9ac2e62e5db4a36fa9f8b591_249_0.png)

FIGURE 9-5 An example of email security settings in Microsoft Outlook.

Outlook, by default, will block active content from untrusted senders and sites, but will allow automatic downloading if the sender is in the “Safe Senders” or “Safe Recipients” lists or the originating domain is in the “Trusted Zone.”

It can’t hurt to be warned before an email client downloads content when a user is editing, forwarding, or replying to an email (as the unchecked security setting in Figure 9-5 displays). Most email clients will automatically download content if the user is replying to or forwarding an email. The assumption is that if the user is doing those activities, they trust the email and its included content. This is not always true. For example, I often forward suspicious emails to a special email account I have set up on my forensics virtual machine to inspect it in a safer, more isolated environment. If I didn’t disable content when forwarding emails, simply forwarding the email there could download content, which is not something I would want to do. So, I would want to intentionally enable the “Warn me before downloading content when editing, forwarding, or replying to email” security option.

## Firewalls

Although firewalls do not stop most of today’s threats, they can stop a minority of threats and some network-based social engineering, and for that alone, they should be enabled by default on networks and endpoints. Host-based firewalls should be enabled on all client endpoints with deny-by-default rules.

## Phishing-Resistant MFA

As covered in Chapter 8, all users should enable phishing-resistant multifactor authentication (MFA) whenever possible to protect sensitive data and systems. About half of social engineering and phishing scams involve trying to trick potential victims out of their login names and passwords. If the user is using MFA instead, all of those password-focused scams will fail. Unfortunately, many of today’s scams involve tricking potential victims out of (or around) their phishing-susceptible MFA, and most MFAs used by most users are susceptible to phishing. Therefore, users should use phishing-resistant MFA to protect their endpoints.

As shared in Chapter 8 and reshared here, these links to related articles by the author provide more information on using and selecting phishing-resistant MFA:

- Don’t Use Easily Phishable MFA and That’s Most MFA! (www.linkedin.com/pulse/dont-use-easily-phishable-mfa-thats-most-roger-grimes)
- My List of Good, Strong MFA (www.linkedin.com/pulse/my-list-good-strong-mfa-roger-grimes)
- Why Is the Majority of Our MFA So Phishable? and US Government Says to Use Phish-Resistant MFA (www.linkedin.com/pulse/why-majority-our-mfa-so-phishable-roger-grimes)

## Password Managers

Unfortunately, if you added up and used all the forms of non-password-based authentication methods, including phishing-resistant MFA, they would not be usable on even 2% of the world’s sites and services. Passwords are still used on the majority of sites and services. So, users will have to use passwords. Strong passwords should be twelve characters or longer if perfectly randomly generated (by a program) or twenty characters or longer if created by a human, to be as secure as possible. This is because password-guessing and password-hash cracking programs are able to successfully crack lesser passwords.

To read all about password attacks and why your passwords need to be long and random, read the author's whitepaper on passwords: www.knowbe4.com/hubfs/Password-Policy-Should-Be-EBook-WP_EN-US.pdf.

Users should use a trusted password manager program to create, store, and use long and perfectly random passwords. There are dozens of different password manager programs to choose from and nearly all do a fairly good job of generating, storing, and using strong passwords, although some are better than others. You should be using a password manager. Encourage or require that other users use a password manager program for every password they can.

Figure 9-6 shows my recommended authentication/password policy.

For more information on password managers see the following author articles:

- https://blog.knowbe4.com/what-about-password-manager-risks
- www.linkedin.com/pulse/password-managers-can-hacked-lots-ways-yes-you-should-roger-grimes
- www.linkedin.com/pulse/browser-based-vs-os-based-standalone-password-managers-roger-grimes
- www.linkedin.com/pulse/hackers-really-cracking-20-character-passwords-roger-grimes
- www.linkedin.com/pulse/another-reason-like-password-managers-use-different-logon-grimes
- www.linkedin.com/pulse/malware-more-often-targeting-password-managers-roger-grimes
