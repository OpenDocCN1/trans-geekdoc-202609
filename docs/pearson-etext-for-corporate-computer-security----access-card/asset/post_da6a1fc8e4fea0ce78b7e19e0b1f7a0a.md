
- 10. Click the Verify All button. (Browse to your downloads directory if necessary.)
- 11. Click OK.
- 12. Take a screenshot.
- 13. Create a new text file named YourNameHash.txt, and save it in your downloads folder. (Replace YourName with your first and last names.)
- 14. Open the text file labeled YourNameHash.txt you just created in your downloads folder.
- 15. Add your name to the contents of the text file.
- 16. Save your changes to that text file by clicking File and Save.
- 17. Close the text file.
- 18. In the FileVerifier++ window, click Verify All again. (Browse to your downloads folder if necessary.)
- 19. Scroll down until you can see the text file that you changed. (It should be highlighted in red.)
- 20. Take a screenshot.

- 3. Double-click on the policy labeled “Audit account logon events.”
- 4. Select both Success and Failure.
- 5. Click OK.
- 6. Double-click on the policy labeled “Audit logon events.”
- 7. Select both Success and Failure.
- 8. Click OK.
- 9. Take a screenshot.
- 10. In the control panel, click System and Security, Administrative Tools, and Event Viewer.
- 11. Click Windows Logs and Security.
- 12. Take a screenshot.
- 13. Log off your computer (you don’t need to shut down) by clicking Start, the drop-down menu next to Shut down, and Log Off.
- 14. Log onto your computer by clicking your username and entering your password.
- 15. In the control panel, click System and Security, Administrative Tools, and Event Viewer.
- 16. Click Windows Logs and Security.
- 17. Take a screenshot.
- 18. Double-click on the Logon/Logoff event that was just recorded.
- 19. Take a screenshot.
- 20. Click Close.
- 21. Click Applications and Services Logs and Microsoft Office Sessions.
- 22. Click on one of the log events.
- 23. Take a screenshot.

## Project 2

Good administrators check their logs regularly. They need to know what went on when they were away. They need to look for intruders, compromised machines, stolen or deleted files, and so on. The list of things to look for can be extensive.

Microsoft Windows Event Viewer® is a simple program that organizes these logs in a way that makes them easy to view. Learning how Event Viewer works is a great training platform for beginners. It is also a useful diagnostic tool.

In this example, you will enable logging of security events, log in and out of your machine, and then look up the event in Event Viewer.

- 1. Click the Windows Start Menu and search for Local Security Policy.
- 2. Click on Local Policies and Audit Policy.

## Project 3

On the Internet, use a search engine to find a security baseline for Microsoft Windows 10. List the title, the organization, and the URL. Briefly describe what is in the baseline.

*Note:* Not all sources use the term *baseline*.

## Project Thought Questions

- 1. Will these security logs track failed logon attempts? From remote machines too?
- 2. Will it track security events other than just logon/logoff events?
- 3. Can you use Event Viewer to view other logs?
- 4. Why is there a log that tracks which Microsoft office programs you use and how long you use them?
- 5. How could a top-notch hacker keep you from knowing which files were changed?
- 6. Can you calculate a hash for a single file?
- 7. From the hash could you tell what was changed in the file?
- 8. Can you use the longest hash possible? How long is good enough?

## Case Study

### New Platform, New Problems

Traditionally, computers have come in the form of mainframes, desktops, and laptops. More recently, we have seen a surge in IoT devices, tablets, smartphones, webcams, and printers. Interconnecting these new devices brings a whole set of new opportunities and threats. Security issues become even more concerning when you have smart cars, home appliances, watches, and glasses.

Microsoft HoloLens® is one of these new devices. HoloLens is a wearable IP-enabled computer that has all the functionality of a laptop computer and more. It can take and send pictures and video. It can also share live video feeds, connect to external data sources, and send messages. For consumers, it’s a dream come true. For a corporate CSO, it’s a nightmare. How do you secure a corporation’s intellectual property, proprietary processes, confidential communications, and new product development from a device that can instantly transmit them around the world?

Even worse, how do you harden Microsoft HoloLens from attackers? Recent articles have shown how Microsoft HoloLens could be hacked, giving full access to anyone who has control over the device. A hacked device could then be used to watch and listen to everything you do. Even if a user is trustworthy and well intentioned, they may not be careful about keeping their possessions secured at all times.

Neil McAllister at *The Register* notes that a variety of potential vulnerabilities may arise if a hacker gains access to a mixed reality device. These vulnerabilities may include viewing your passwords, PINs, or door codes as you type them.

Microsoft HoloLens is just one of the upcoming smart devices that raise new security concerns. Nearly all auto manufacturers, including tech companies like Google (Waymo), are developing a self-driving car. It’s not hard to imagine a self-driving car with Microsoft HoloLens–enabled features. Would facial recognition be allowed? If so, how would that affect privacy?

In a recent annual report¹⁹ by Sophos, some of these new host-related security issues were discussed. The following are five key points from their report:

- 1. **Mobile Data**—No doubt, the increasing mobility of data in corporate environments is one of the biggest challenges we faced in the past year. Users are fully embracing the power to access data from anywhere. The rapid adoption of bring your own device (BYOD) and cloud practices are really accelerating this trend and providing new vectors of attack.
- 2. **Diverse Platforms**—Another trend we are seeing is the changing nature of the endpoint device, transforming organizations from a traditional homogeneous world of Windows systems to an environment of diverse platforms. Modern malware is effective at attacking new platforms, and we are seeing rapid growth of malware targeting

mobile devices. While malware for Android was just a lab example a few years ago, it has become a serious and growing threat.
- 3. **BYOD**—BYOD is a rapidly evolving trend, and many of our customers and users actively embrace this trend. Employees are looking to use their smartphone, tablet, or next-generation notebook to connect to corporate networks. That means IT departments are being asked to secure sensitive data on devices they have very little control over. BYOD can be a win–win for users and employers, but the security challenges are real while boundaries between business and private use are blurring. It raises questions on who owns, manages, and secures devices and the data on them.
- 4. **Web-Based Malware**—Finally, the web remains the dominant source of distribution for malware—in particular, malware using social engineering or targeting the browser and associated applications with exploits. For example, malware kits like Blackhole are a potent cocktail of a dozen or more exploits that target the tiniest security holes and take advantage of missing patches.
- 5. **Evolving Security**—IT security is evolving from a device-centric to a user-centric view, and the security requirements are many. A modern security strategy must focus on all the key components—enforcement of use policies, data encryption, secure access to corporate networks, productivity and content filtering, vulnerability and patch management, and, of course, threat and malware protection.

In addition to these trends, Sophos’s annual report also issued some statistics about the percentage of PCs that experienced a malware attack within a 3-month period.²⁰ Corporations with offices in certain countries may need to take additional steps to harden hosts in those locales.

### Case Discussion Questions

- 1. How could new smart devices pose a security risk for a corporation?
- 2. How could corporations guard against threats from new smart devices?
- 3. Could a ban on all smart devices from outside the corporation be a workable policy? Why or why not?
- 4. Why is data mobility a security threat to businesses?
- 5. How will diverse computing platforms affect IT security?
- 6. How must IT security evolve to address the development of new devices?
- 7. Would IT security policies need to be adjusted for corporate offices in different countries? Why or why not?
