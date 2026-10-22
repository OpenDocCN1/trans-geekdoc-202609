
## 35.12 SECURING P2P, IM, SMS, AND COLLABORATION TOOLS

causes users to do just about anything they can to accomplish their goal of unobstructed IM. Some clients are designed with this in mind and will happily tunnel out of commonly allowed TCP/IP ports such as 80, usually open for HTTP communications. The software may be configured to bypass firewall rules, detect and avert packet-shaping technology, and tunnel its way to the Internet via encrypted connections. Many IM services also provide Web-only interfaces that do not require software to be installed while communicating via HTTP. Unfortunately, this technology can be a difficult and frustrating one to ban within the organization; a complete ban is probably not a practical solution.

### 35.4.2.3 Prevent Installation of Instant Messaging Software.

Although a complete ban may not be possible, or even desirable, one step that a more secure organization can take is to prevent users from installing IM software. This tactic is not going to solve the whole problem, but it certainly will help. Controlling the installation of IM software should be part of the organization’s overall software installation policy. In general, installing software without permission should be denied. If it is feasible, local workstation administrator rights should be denied for most employees. In many user or system management solutions, it is also possible to block software installation through individual, group, or workstation policy templates and procedures. Universal software installation prevention is much easier than trying to define policies or templates for every possible IM peer, application, group, or tool.

### 35.4.2.4 Fight Technology with Technology.

Technology on its own will not provide the organization with an all-in-one solution for securing IM. However, there are a number of network devices, appliances, traffic monitoring software, and other technologies to help an organization minimize IM use. Do not believe marketing claims that any device or technology can guarantee IM blocking: few can deliver on this promise. The only true way to guarantee an IM-free company is to block access to the Internet completely—which is not realistic. An organization can also leverage existing security infrastructure such as IDS or IPS.

### 35.4.2.5 Limit Risk and Exposure.

For most organizations, limiting IM through policy and technology is the solution to the threats that IM introduces. Combining those two approaches will help to reduce the possibility of data loss. Security managers and administrators should agree on what can and what cannot be allowed within the organization. An organization may choose to block file transfers, Webcam functions, or screen-sharing functions for IM communications. These types of actions will not prevent IM security breaches, but they could limit data loss. As with any policy and risk management, proper audit, reporting, and compliance controls must be in place.

### 35.4.2.6 Providing Secure Instant Messaging.

In environments where IM is needed to run the business, the best strategy is to provide secure, managed IM services to the employees. Of course, the needs will vary among different organizations for different levels of IM connectivity, functions, and software. Many of today’s popular corporate email and collaboration systems have built-in or optional IM services. When properly deployed, these IM systems can meet many of these secure IM best practices:

- Encrypt IM communications wherever possible: client to server, server to Internet, and so on.

responsibilities and liabilities of both parties should be carefully weighed by information security managers, company executives, and legal counsel before allowing use of the software and associated services.

## 35.5 SECURING SMS.

Few technologies are more ubiquitous than SMS. Virtually all mobile phones are capable of sending and receiving SMS communications. Since mobile phones are virtually everywhere, security considerations must be in place to guard against the threats that they present. A technology with a relatively minor footprint can cause a world of destruction when used as a weapon. Today, SMS technology, and its associated complementary services, has grown exponentially. Securing and defending against SMS must be included in every organization's comprehensive security plan.

To understand SMS security, it is also important to look beyond the cell phone. SMS does not require a cell phone to utilize the technology. Many phone carriers allow SMS messages to be generated and sent from an unsecured, public Website. SMS messages may also originate from email messages, instant messaging services, and the like. SMS messages can even come from subscription services such as a daily horoscope or critical systems like emergency notification services. Beyond this, today's mobile phones, including smart phones, are more powerful and contain many more features and show no sign of slowing down. Phones are increasingly gaining processing power, memory, complex operating systems, and other features that essentially could redefine the device as a personal computer. Phones are able to access the Internet, install applications, communicate from phone to phone, and even access corporate data networks. Information security managers and professionals should never underestimate the power or versatility of a mobile phone. They are a threat to all of an organization's information security.

### 35.5.1 Dangers to the Business.

SMS can introduce many types of security threats into an organization. SMS can cause a data breach by innocent mistakes or by deliberate attacks. This technology can be used as a criminal tool to deliberately steal information, to extract data, to extort information, and to deceive. It may also be a conduit for inadvertent data loss. The consequences of data lost via SMS are relatively the same as any other data breach: loss of confidence in the organization, loss of image, bad public relations, financial penalties, and so on. A serious or even minor data breach may appear to communicate to the world that the organization does not have a comprehensive security plan in effect, or the company does not abide by such a plan—whether true or not. Some investors, customers, or people in the general community may look at a breach of such a simple technology and ask, "How could the company not have proper security for something as simple as a cell phone?" A missing laptop with confidential data is a serious security breach, but a mobile phone, with all its capabilities, must be treated as nearly the same type of critical infraction.

### 35.5.1.1 SMS as a Tool for Deliberate Data Loss.

One danger an organization may face involves an individual or group of people utilizing SMS technology to ferry critical data to unauthorized persons, usually outside the organization. This action would replicate an age-old tactic of stealing information piece by piece from within the organization to someone who should not possess the information. Consider classic tricks of criminals, such as copying information in tiny pieces over great amounts of time to avoid causing suspicion. Any number of technologies can be used to move data, including flash or thumb drives, iPods, scraps of paper, photographs, screen printouts.

and more often, that device is an unmanaged Apple iPhone or Google Android variant smartphone.

Employees will want to connect their smartphone to the organization’s email and calendaring system, as well as utilize the Wi-Fi infrastructure. They will want to stay connected for professional reasons (corporate email keeps them connected to the office and more productive), connected for personal reasons (personal email, social networking), and utilize battery-saving Wi-Fi instead of the cellular data networks. On the flipside, they may want to use their phone to tether another wireless device via Wi-Fi where they cannot or are not allowed to connect to corporate Wi-Fi.

This, combined with the knowledge these devices are unmanaged, have almost unlimited unknown applications, or "apps," and basically are small mobile computers, is enough to make most security pros wince. It is increasingly difficult to tell employees "no" when it comes to them utilizing these devices in the workplace, especially when they are sometimes required to do so for their job. This new challenge must be addressed in the organization’s policy for mobile phones/mobile computing. It should be strictly laid out what is allowed, what is not, and how the rules will be enforced. Device management features should be utilized when allowed by the organization’s platform to control things like encryption, email sync, data retention, device passwords, and device lock-out.

### 35.5.2.5 Other Considerations.

The next list provides points to consider when planning for SMS security, many of which are from NIST Special Publication 800-48, "Wireless Network Security."11

- 1. Create policies and procedures to deal with lost mobile phones. The phone may contain sensitive data, including stored and deleted SMS messages.
- 2. If cell phones are banned from the organization’s premises, ensure that physical security has procedures and rules for checking visitors and employees for mobile phones.
- 3. Many mobile phones have the capability to back up and synchronize their contents to the desktop. Ensure proper procedures to secure data and data leakage.
- 4. Policies and procedures should be in place to limit and manage the acquisition of mobile phones by employees—information security may not be aware of the existence of new phones in the environment.
- 5. Mobile phones are not easily audited, nor is there much software to aid in the auditing process.
- 6. Despite proper labeling of a company-owned device, if lost it will rarely be returned to the organization. Plan to mitigate damage caused by a lost mobile phone; utilize security features such as remote wiping the device after loss via "poison pill" features or "auto-destruct" features after several invalid password attempts.
- 7. If a mobile device supports screen-lock and power-on passwords, use these simple protections wherever possible.
- 8. Through policy and education, prevent as much sensitive and private information on the organization’s mobile phones as possible, including SMS messages.
- 9. Utilize Public Key Infrastructure (PKI) technology where possible.
- 10. Install antivirus software where possible.
