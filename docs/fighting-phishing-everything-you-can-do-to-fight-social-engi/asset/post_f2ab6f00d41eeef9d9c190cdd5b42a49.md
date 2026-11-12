
as widely known or deployed. Hopefully, readers got introduced to one or more technical defenses they could deploy in their networks or on their servers to help mitigate social engineering and phishing.

Chapter 9 will cover anti-phishing defenses that can or should be deployed at the endpoint or client level.

## CHAPTER 9 Endpoint Defenses

Chapter 9 will cover defenses that can be deployed on client endpoint computers and devices to fight social engineering and phishing.

### Focusing on Endpoints

Endpoints are nodes connected to a network. They can be almost anything but are often used to refer to end-user devices and computers. Most of the data we are trying to protect is either located on an endpoint or accessed through an endpoint. All our other defenses, located anywhere else, are trying to protect the data located on endpoints and users using endpoints.

Much of this chapter is going to be a repeat of cybersecurity defense recommendations made in previous chapters (especially Chapter 8, “Network and Server Defenses”), because a great defense-in-depth, multi-layered cybersecurity defense places similar good defenses in multiple places (i.e., network and endpoint). But there will be many recommendations that can only be deployed on endpoints that will be discussed in this chapter. The idea of this chapter is to remind readers of all the possible endpoint defenses that could be used to fight social engineering and phishing and, if lucky, possibly remind you of something you agree with but previously missed.

## Anti-Spam and Anti-Phishing Filters

Every endpoint capable of getting phishing messages should have anti-spam and anti-phishing filters installed. Most of the time, this means content filters on email and browsers, but expand that to whatever applications you have where you could get phishing messages (e.g., SMS, Microsoft Teams, Slack, collaboration apps, etc.).

## Anti-Malware

Every endpoint should have anti-malware software installed. Typically, this means antivirus software but can also mean installing and using endpoint detection and response software. Most endpoints should have both. Each will capture and block what the other might miss. Both types of software programs should, of course, be kept up-to-date.

## Patch Management

The second most common reason for cybersecurity compromise is hackers or malware exploiting unpatched software or firmware. All endpoints should have all critical patches applied within one to two weeks of being released by the vendor. It is super important that if an endpoint has a vulnerability listed on CISA's Known Exploited Vulnerability Catalog list (www.cisa.gov/known-exploited-vulnerabilities-catalog) that it gets patched ASAP! CISA only places vulnerabilities that are being actively exploited against real-world organizations by hackers and malware.

## Browser Settings

Most Internet browser settings have fairly strong default security settings. If those settings aren't weakened, they are usually good enough to prevent most malicious manipulation of a browser by social engineering and phishing. This isn't always true, and I'll be covering some interesting hacker browser tricks in Chapter 13, “Recognizing Rogue URLs.” But make sure you did not accidentally weaken browser security settings below their initial defaults.

## Browser-Within-a-Browser

One of two interesting hacker malicious browser tricks I want to cover here is known as browser-within-a-browser. It can't necessarily be stopped using a browser security setting. It's more that it must be looked for and noticed by an end user to prevent it. Browser-within-a-browser attacks are when a hacker presents what looks like an entirely different browser window to a user (representing a particular URL), but it isn't a new browser window. It's just some HTML code and content made to look like a new browser window, but entirely contained in the same original browser window.

We are all used to going to websites that, for some reason or another, open up additional browser windows for us to interact with. Many times, it's because we went to log on to a particular website or clicked on a particular logon option (such as Login with Facebook), and the original website then opened up a new browser window to the other logon on another website. Figure 9-1 shows a legitimate example of that particular, non-malicious, situation:

![](img/49fb1c0c9ac2e62e5db4a36fa9f8b591_243_0.png)

FIGURE 9-1 An example of a browser window on one website opening up another browser window on another website.

Figure 9-1 shows a non-malicious example of a website opening another browser window to another website. In the example, I went to www.bestbuy.com, started to log on to my BestBuy account, then chose the offered alternative logon option, “Sign In with Google.” When I clicked that logon option, BestBuy’s website opened up another browser window to google.com so I could sign in using my Google account credentials. This is normal and legit. A website opening up another browser window is normal. If I type in my Google account credentials, in this example, those credentials would be captured and acted upon by google.com, and not the first website. This separation of URLs is very important for logon safety. You don’t want the first website, which may have nothing to do with google.com to get your login credentials to your Google account. Instead, the first website sends the user to google.com, the authentication happens there, and then the original website gets told the authentication event at google.com was successful, trusts it, and lets the user onto their website.

But the whole process can be simulated. Instead of opening up a second browser window to the second website, malicious browser-within-a-browser attacks fake the entire experience, fooling the user into providing their secondary login credentials to the first malicious (or compromised) website. Malicious phishing websites will change their existing webpage that the user is currently viewing to look like they are opening a second browser window linked to a second website but are instead just showing what looks like a second browser window. It’s just for show, and most importantly, still linked to the first, malicious website. So, if an end user was tricked into inputting their Google account credentials, in this example, then those Google credentials would be inputted into and stolen by the first website.

For more information and examples on browser-within-a-browser attacks, see the following:

- www.techrepublic.com/article/browser-in-the-browser-attacks-arise
- https://mrd0x.com/browser-in-the-browser-phishing-attack

The defense against browser-within-the-browser attacks is to be aware of them, and always make sure if you get what looks like a secondary browser window that it is a real secondary browser window and not a fraudulent look-alike. Also, using MFA, passkeys, and password managers, where you don’t manually enter your login credentials, can help.

## Full-Screen Mode

Another common technique malicious hackers and phishers use on malicious websites is forcing the user’s browser into “full-screen mode,” which converts the normal browser window with a frame and heading into a full-screen presentation without a frame or heading. This is usually done in conjunction with a hyper-aggressive warning of a (fraudulent) malware infection or a fraudulent warning supposedly from the FBI or law enforcement, known as scareware. Figure 9-2 shows an example of a full-screen scareware warning.

Sometimes the involved website includes code that can make the cursor disappear or the keyboard become non-responsive, giving the full-screen display the appearance of having locked up the computer.

See this link to see a test example of the issue on your browser: https://webdbg.com/test/fullscreen.

![](img/49fb1c0c9ac2e62e5db4a36fa9f8b591_246_0.png)

FIGURE 9-2 An example of a full-screen scareware warning.

Computer-savvy people have usually seen this type of trick enough that they don’t panic. They hit the escape key (Esc) to regain control or might even need to kill the browser instance or restart the computer. But they know the computer isn’t in some “full control mode” where they can’t regain easy control. Less knowledgeable users don’t have the same understanding and often fall for the trick and follow the screen’s commands. Make sure your security awareness training covers this easy-to-defeat, but sometimes frustrating, scam.

## Browser Notifications

As previously covered in Chapter 2, “Phishing Terminology and Examples,” browser notification phishing is a particular type of phishing that originates from the user’s operating system or browser notification features. Most of today’s most popular operating systems and browsers have an industry-standard message notification feature built into them, which allows websites and apps to ask for permission to send messages (see Figure 9-3 for an example).
