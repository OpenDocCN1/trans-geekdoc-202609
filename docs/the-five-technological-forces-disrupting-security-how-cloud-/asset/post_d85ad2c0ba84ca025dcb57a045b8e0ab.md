
trusted computing device that is already inside a corporate network, the attacker has already breached the first line of perimeter defense—the firewall. From here, the trusted device with the (now) malicious software is in a much stronger position to explore the network and compromise some device and information systems.

While not high profile as cybersecurity risks, technical and behavioral changes from new software releases are equally problematic on a purely functional basis. Security integrators are accustomed to seeing the integration between systems broken when one of the vendors releases new software. For example, information exchange between a video management system and an access control platform may stop working when one is updated. Vendors have legitimate reasons for changing the APIs or SDKs that create these integrations possible, but the lack of coordination among manufacturers creates numerous disruptions for users of previously deployed systems. As the number of connected devices and integrations goes up, these problems become more frequent.

The success of IoT in physical security depends in part on establishing an effective software update to these systems. For the software companies and manufacturers who create these systems, there are deeper issues around coding practices, cryptography, penetration testing, zero-day vulnerabilities, and more subjects than I can possibly list.

## A PATH FORWARD

I could list the points of vulnerabilities in our current ecosystem and run around crying the sky is falling. This type of alarmism is a staple of most panel discussions at industry conferences. What is far more difficult to suggest a course of action that moves the discussion forward and gives security organizations some practical guidelines that they can use. To end, I have three proposals that I hope move the dialogue forward.

First, we need to agree on some minimum standards for device security. There are many models and existing reference works to choose from, so we don't need to start from scratch. A great example of how this can work is what the payments industry did with PCI compliance. Standards could be tailored for the unique risks posed by cameras, controllers, readers, and other common security devices.

Second, voluntary testing is a way for companies to distinguish themselves and show customers that they care enough about cybersecurity to have their products certified. Mandatory testing would face huge resistance, but voluntary compliance offers the ability of leveraging peer pressure and market forces to accomplish the same goal in a much less painful way.

Finally, security organizations need to be able to find out whether the security products in their properties pass muster. This is one of the issues I heard directly from a security practitioner in one of my ASIS audiences. He said they often lack a connection to the manufacturer of a particular device because their integrator mediates the relationship and they don't always forward information about product vulnerabilities. For this, we need public registries like the NIST CVSS for software-related cyber vulnerabilities.

## IoT Technology and Standards

IoT and industrial automation devices use hundreds of communication protocols, security, and interoperability standards. This diversity of technologies presents a wealth of choices and a tangle of interoperability issues. We'd all like to see plug-and-play simplicity, but when was the last time that happened?

Standards can be a very dry topic. You might wonder which ones matter and why you should care about them. I'll be the first to say that you don't need to keep track all of them. Like technology itself, standards are layered on top of each other. There are low-level standards for things like electric impulses or radio waves and high-level standards for data formats and handshakes between computer systems. The higher standards often make unnecessary to understand the lower layers, or they work with multiple versions of lower layers (which amounts to the same thing).

Your role in security will determine which types of standards matter to you. If you are an engineer for a security product company, then lower layer standards will be important to make your product work at all. If you are a product manager, you will be interested in what types of standards are being adopted—where in the industry and what that means for your product road map. If you are an integrator, you will want to make sure that the products your company has chosen represent all work with one another. And if you are an end user in a security organization, you will want to know enough about standards to make your integrations and manufacturers have a standards strategy that gives you a reasonable chance of future-proofing the choices you make today.

Our goal is to sort some of the standards that matter at the highest level for security organizations, with at least a glimpse into the next layer. We could have covered the topic of standards in almost any section of this book, but they appear to come together and be most relevant in the context of IoT. Cloud standards are important, but cloud systems are easy to reprogram as the word changes around them and can mostly be done with little customer impact. Mobile standards are also important, but they are already well down to a handful of choices by the carriers and phone manufacturers. In IoT,

## CHAPTER 10: IoT Technology and Standards

however, we find ourselves in the familiar territory of large population's hardware devices geographically distributed and difficult to change out if we make poor standards choices early in the game. IoT standards also depend on cloud, mobile, and cyber standards, and so they pull a lot of threads all in one place. Allow me to highlight the aspects of emerging standards important to decision-makers as this new market goes through its burn-in period.

Plug-and-play simplicity requires agreements about standards, and standards can only exist where there are common visions of how systems be put together—in short, their architecture. Standards have been an essential part of building the modern world, from bridges and skyscrapers to telecommunications and electric grids. They require agreement about how the pieces fit together.

The first order of business is to understand what those pieces are—which technologies drive or enable the rise of IoT. Much of it will prove familiar to anyone versed in the electronic sector or consumer electronics business. What has changed is the way that familiar components have been reorganized into updated architectural paradigms. New roles and relationships among the parts of a system create the need for new standards on how they communicate and interact. An old shoe't always fit a new foot.

For consumers, there's a lack of transparency in IoT. Most popular literature doesn't spend a lot of time explaining interoperability and security protocols follow, if any. This leaves the buyer in the dark. In many cases, it is challenging to evaluate the interoperability and security of new protocols and authentication mechanisms. Many are too young to be fully shaken out in real-world conditions. In practical terms, no security organization or system integrator can be expected to know how all of these devices will operate and which configurations and combinations are securable. You will need to pick a subset and become familiar with those.

Many IoT devices are dangerously insecure. You could say they are insecure by design or by the lack of design. One reason is that many of small computing environments do not have the resources to run the kind of good security defenses available for standard operating systems and network stacks. Another reason is to support a sufficient investment in cybersecurity or verification testing. Untested is unsafe until proved otherwise.

We talked about the software update treadmill early, but that's not the worst of it. Many simple IoT devices have no provision to upgrade their

¹With apologies to those interested in video surveillance, we will only be mentioning those standards in passing. Between ONVIF and MPEG, they are widely accepted and well covered by both organizations.
