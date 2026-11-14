
![](img/5f597c6a70133069118d9e804ace3775_193_0.png)

DNS redirectors can also be set up with socat or iptables. Along the same lines, domain fronting can be used to route traffic through high-trust domains like Google App Engine, Amazon CloudFront, and Microsoft Azure. Traffic can be routed through legitimate domains using domain fronting, including .gov top-level domains (TLDs)!

## Adaptive Testing

Although stealth activities are a big part of red team assessments, there’s a lot of value in taking an adaptive testing approach. The stealth activities in a red teaming engagement closely mimic what an advanced adversary would do. However, adaptive testing takes the perspective that there’s value in performing simulations that mimic unsophisticated adversaries too—adversaries that are easier to detect than others.

Because longer-term red team assessments allow for testing cycles, an organization can set a certain cadence to its work to build in an “adaptive testing” perspective and move from clumsy, noisy attacks to testing activities that are stealthy and silent. For example, a three-month testing cycle can be performed where activities progress from easy to detect to hard to detect. After the three-month cycle, outbrief meetings and a post-mortem analysis can occur, and the blue team can gain perspective on at what point testing activities stopped being detected or stopped “hitting its radar.” The blue team would then use this information to mature its detection capabilities. The next three-month cycle could then begin, giving the blue team the opportunity to test the improvements it has made.

Many different tactics can be used to employ an adaptive approach. You can begin testing by sending out a large phishing campaign to measure how the organization responds and then move to a quieter spear-phishing attack. Scanning activities can begin with aggressive scanning tactics and move to a low-and-slow approach.

## External Assessment

Many people automatically think of a perimeter security assessment when they hear the term penetration test or red team engagement. Although it is not the only component of a red team engagement, performing adversarial emulations on your perimeter is very important. When I think of a red team engagement with an external focus, I think of the importance of understanding what a bad actor anywhere in the world could do with a computer.

Most red teaming activities will combine using tools to scan the environment for information and then using manual testing activities and exploits to take advantage of weakness identified. However, this is only one part of an external assessment. It’s important to also remember that there can be a “near site” component to a red team exercise, where the red team can show up in person to perform attacks. In addition to Internet-accessible resources, the red team should ensure it is looking for weakness in an organization’s wireless environment and vulnerabilities related to how mobile technology connects to an organization’s technical assets.

External assessments can focus on any IT asset that’s perimeter facing, including e-mail servers, VPNs, websites, firewalls, and proxies. Often an organization will have exposed internal protocols that aren’t intended to be exposed to the Internet, such as the Remote Desktop Protocol (RDP).

## Physical Security Assessment

Protecting physical access to an organization’s devices and networks is just as important as any other security control. Many red teaming engagements find problems with the way that locks, doors, camera systems, and badge systems are implemented. Many organizations can’t tell the difference between an easy-to-pick lock and a good door lock and protective plate. Lock picking is a skill that most red teams will have because picking locks is a relatively easy skill to learn and grants unparalleled access to a target.

Motion detectors often open or unlock doors when someone walks past them. This feature is also convenient for attackers attempting to gain physical access to an organization. Many red team assessors have manipulated motion detectors to gain physical access. It can be as easy as taping an envelope to a coat hanger, sliding it between two doors, and wiggling it to trigger the motion detector on the other side of the door. Compressed air can also be used to trigger motion detectors.

Many physical security badges lack encryption. A favorite tactic of red team assessors is to obtain a badge cloner and then go to the local coffee shop or deli and stand in line behind an employee who has a physical security badge. Badge cloners are inexpensive, and all it takes to use one is to stand within three feet of the target to be able to clone their badge and gain the same level of physical access to the organization’s facilities.

Camera systems often have blind spots or resolution that’s so poor that a vehicle’s license plate isn’t legible when captured by the camera. Touchpad locks rarely have their codes changed. Wear and tear often causes fading so that simply looking at the lock can reveal which four numbers are used in the code. All an attacker has to do then is enter the four digits in the right order.

The possibilities for physical compromise of an environment are endless, and like red teaming activities, they are only limited by your imagination.

### Social Engineering

Humans will always be your security program’s weakest link. They are by far a red team’s easiest target. Humans can be targeted via phishing e-mails, USB drives, phone calls, and in person. Consider purchasing inexpensive pens or eyeglasses that contain cameras and replaying video of your in-person social engineering attempts for your client or organization.

Phishing e-mails can be crafted to be very high quality with spoofed e-mail addresses and an impressively accurate look and feel. There’s also a benefit to seeing how users respond to poorly crafted e-mails with generic greetings and misspellings. The two components to phishing are delivery and execution. Object linking and embedding (OLE), .iso files or ISO images, hyperlinks, and e-mail attachments are common payload delivery mechanisms, and .lnk files, VBScript, JavaScript, URL, and HTML applications (HTA) are common payloads.

When attempting to gather information about your target, don’t underestimate the effectiveness of developing online personas for use in social networking or in other capacities. Cat phishing is a term that describes creating enticing profiles online and then selectively making connections with your targets. The anonymity of the Internet means that people need to be wary of their new online friends. People also tend to disclose a surprising amount of information via tech forums, for example.

Finally, don’t be afraid to hide in plain sight. Consider performing a somewhat noisy attack with the intention of getting caught as a distraction for a stealthy attack that you are carrying out using a different tactic.

### Internal Assessment

To my surprise, organizations sometimes still have to be convinced of the value of an internally focused red team assessment. An internal assessment can mimic a malicious insider, a piece of malware, or an external attacker who has gained physical access. An internal assessment is a great way to gauge how your protections stand up to a person who has made it onto your network.

A person with no credentials but access to a network port can gain a ton of information if the environment is not configured correctly. A variety of man-in-the-middle attacks can prove fruitful when you have access to the wire. SMB relay attacks and Windows Proxy Auto-discovery (WPAD) attacks are consistently effective in leading to credential harvesting, privilege escalation, and frequently the compromise of an enterprise.

Once you have code running in the desktop session of a user, many mechanisms are available to put a keylogger on a machine or to capture screenshots. Using Cobalt Strike’s Beacon is an extremely reliable method. The custom-written Start-ClipboardMonitor.ps1 will monitor the clipboard on a specific interval for changes to copied text. KeePass, a popular password safe, has several attack vectors (including KeeThief, a PowerShell version 2.0 compatible toolkit created by @tifkin_ and @harmj0y) that can extract key material out of the memory of unlocked databases. However, KeePass itself contains an event-condition-
