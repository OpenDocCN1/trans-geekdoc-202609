
A third difference is legality. As I stated earlier, hacking is not necessarily criminal. And a great many hackers are law-abiding people. However, certainly some hackers are engaged in criminal activity. A penetration tester is never engaged in cybercrime. The penetration tester always has the permission of the system’s owners. In fact, as we will discuss later in this chapter, a clean criminal background and impeccable ethics are must-have qualities for a penetration tester.

## The Hybrid Test

Larger organizations will conduct audits, vulnerability scans, and penetration tests separately. Sometimes these tests are even conducted by separate teams; however, such an approach might not be cost effective for smaller organizations. As I stated earlier, I often begin my penetration test with a few vulnerability scans. In a hybrid test, one first expands that initial vulnerability scan and includes the reports of that scan in the final penetration testing report.

It may also be useful to preface your test with a brief review of policy compliance and past incident reports. The final product of these steps is to have a penetration test that includes a vulnerability assessment and a brief audit. This can often be a cost-effective solution for smaller organizations.

## Terminology

Before we go much further, it is important that you understand basic terminology used in the hacking and penetration testing communities. Some of these terms are in very wide use, and you are likely to have heard of them before. Others will be less common, possibly new to you.

- **Ad hoc testing:** Testing carried out with no systematic approach or methodology. It is hoped that this book will steer you away from that.
- **Black hat hacker:** A hacker who does break the law. This term is synonymous with cracker, but the term *black hat hacker* is far more common. Contrary to some media portrayals, a black hat is not necessarily any more skilled. Someone can break the law and still have only minimal skill.
- **Cracker:** One who breaks into a system in order to do something malicious, illegal, or harmful. Synonymous with black hat hacker.
- **Ethical hacker:** Someone who is using hacking techniques for legal and ethical purposes.
- **Footprinting:** Scanning a target to learn about that target.
- **Gray hat hacker:** A hacker who usually obeys the law but in some instances will cross the line into black hat hacking.
- **Hacker:** One who tries to learn about a system by examining it in detail by reverse-engineering or probing the system. This is an important definition. Hackers are not necessarily criminals. One can be a hacker and never break the law, nor do anything unethical.
- **Script kiddy:** A slang term for an unskilled person who purports to be a skilled hacker. Some people download a tool or two, learn to use those, then consider themselves great hackers, when they are not.
- **White hat hacker:** A hacker who does not break the law, often synonymous with ethical hacker. Essentially this is a person who uses hacking skills in a legal and ethical manner.

These are basic terms, and you will see others introduced in the text as we go along. Another issue that must be addressed along with terminology is the hacker culture. Again, I will stress that while penetration testing and hacking are closely related, they are not the same thing. This may make you wonder why you need to be concerned about the hacker culture. The fact is that you can learn a great deal from hackers. Therefore, an understanding of the hacking culture can be very useful.

The hacking culture is generally one of exploration. Yes, there are some people in the hacking community who commit crimes, but that is not all, nor even most, of the hacking community. In fact, there is not an organized, uniform “hacking community.” The community is incredibly diverse and amorphous. The one thing that binds it together and makes it a community is the desire for knowledge. And that is the key element in the hacker world. Knowledge is king. Among the hacking community, degrees and certifications count very little; what you can prove you know, what you can do, is what is important. This is key if you choose to visit one of the major hacking conventions, such as DEF CON. The attendees are only concerned about learning. And they can be harsh critics when it comes to speakers and presenters. They expect all speakers and presenters to provide new and applicable knowledge.

That aspect of the hacking culture is exactly why it is so critical for you to be connected to it. It is a place where you can learn things, things that are not always published in books and journals. I will, however, reiterate that hacking and penetration testing are not the same things. But penetration testing does require knowledge of hacking techniques. Therefore, knowing as many diverse hacking techniques as you can is critical (and we will explore many of these later in this book).

While I have already stressed (and will continue to stress) that hacking and pen testing are separate but related activities, professional pen testers should take from the hacking community that love of learning. Penetration testing, vulnerabilities, and system security in general are constantly changing. If you literally knew everything there was to know about penetration testing today, that knowledge would start to become dated and new knowledge would be needed within 24 months. Some people find that aspect of this profession quite daunting. I find it exhilarating. As a hacker or a professional penetration tester, you are on a lifelong journey of constantly learning. The one constant is that no one (not even this author) ever knows enough. And that hunger to know more is the defining characteristic of the hacking community.

## Methodologies

Methodology is one of the key elements that separate penetration testing from hacking. What approach do you use to perform a penetration test? There are various general approaches we will examine first, then we will delve into more specific methodologies. Methodology is separate from penetration testing standards, which we will cover in Chapter 2, “Standards.”

### Nature of the Test

There are three broad categories of penetration testing. They are usually termed black box, white box, and gray box. These designations are a description of how much information the penetration tester is given prior to the test.

### Black Box

A black box test involves the penetration tester having as little information about the target network as possible, perhaps only the organization’s name and URL or IP address of their gateway router. The goal of such tests is to simulate an external attacker attempting to breach the network. Obviously, a black box test must be done by an outside party, as any member of the organization’s own IT department would have some knowledge of the organization’s network.

As with any approach to testing, there are benefits and drawbacks to black box testing. One benefit is that it does exactly mimic an outside attack. A second benefit is that the skill of your penetration tester will become immediately obvious. If they are not very skilled, they may have difficulty making any successful penetration of your network.

The most significant drawback to this approach is that it will always be more costly. It takes significantly more time to conduct a black box test, because the penetration tester must first learn about the target network. Furthermore, he or she must learn by scanning and probing. This all takes time.

### White Box

As the name suggests, this is the complete opposite of the black box test. This approach to penetration testing involves the tester having extensive knowledge of the target system. This will include the following:

- IP addresses of workstations and servers
- Operating system information for computers
- IP addresses for switches and routers
- Information regarding security devices such as firewalls and intrusion detection systems

A white box test can be done by internal or external staff. There are two major advantages to this approach, the first being that it is well suited for your internal staff to perform because they already have some significant knowledge of the network. A second advantage is that this approach takes less
