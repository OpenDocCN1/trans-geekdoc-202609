
criminals. They are all there for the same purpose: to learn. The only problem with DEF CON is that it is so huge, you cannot possibly see everything you want to see.

There are many other hacking conferences today. Black Hat is fairly large, and has a very good reputation. It also runs just prior to DEF CON, and both are in Las Vegas. So, you could come to both on a single trip. DEF CON and Black Hat are the two “must attend” conferences. At some point in your career, you should attend each of these. However, there are many other hacking conferences that are popping up all over the world. One of those might be more conveniently located for you.

ShmooCon is starting to get more publicity. It has been around for a few years and, while not as well known or nearly as large as DEF CON, is an interesting conference.

For the security professional side of things, the ISC2 Security Congress is probably the most well-known security conference. It is held each year in a different city. There is a wide range of speakers on a variety of security topics. You can pick those talks that are of most interest to you.

Also of interest is SecureWorld. These tend to be smaller conferences, but are held in several major cities each year. This makes it more convenient for many security professionals to attend. Like ISC2, you can attend the talks that are of interest to you. The RSA Conference is also well respected, and has been around for quite a long time.

The preceding are just a sample of the most widely known conferences. There are certainly many others that are very good conferences. The way you evaluate whether a conference is “good” or not is simply by how much you learn at the conference.

## Dark Web

The dark web is a critical topic for penetration testing, for several reasons. The first is that there is a great deal of information regarding hacking and breaches available on the dark web. Any penetration testing professional should be familiar with it. The second reason is that dark web markets are often a conduit for stolen data from corporations. Because penetration testing is about network security, it is useful to know something about how to track information on the dark web.

The dark web is an area of the Internet only accessible via onion routing. Onion routing essentially routes packets all around the world, bouncing through proxy servers. Each packet is encrypted with multiple layers of encryption, and each proxy can only decrypt one layer, and send the packet to the next proxy. If someone intercepts a packet in transit between two proxies, you can only determine the previous proxy and the next proxy. You cannot determine the actual origin or destination, as illustrated in Figure 17-1.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_378_0.png)

FIGURE 17-1 TOR.

What this leads to is a situation where one's location is not easily determined. For example, I used the TOR browser to visit Yahoo.com. I did this sitting in my study in Plano, Texas. In Figure 17-2 you can see the results.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_378_1.png)

FIGURE 17-2 Yahoo Through TOR.

As you can see, Yahoo thinks I am coming from Sweden, and presents its page to me in Swedish. This anonymity is not inherently illicit. There are many legitimate reasons one might wish to surf the Internet anonymously. Some people simply do not like being tracked, and it is clear that many companies do track Internet traffic for marketing purposes; however, the TOR browser has also given birth to illicit dark web markets. These are markets on the web where people buy and sell illicit goods. Items are paid for in Bitcoin or similar cryptocurrency, making the purchases very difficult to trace.

One of the reasons, already mentioned, why this is an issue for security professionals, including penetration testers, is that your client’s data could already be for sale on the dark web. Most penetration tests/security audits do not do a dark web audit, but perhaps they should.

Recently, a few major dark web markets have been taken down by law enforcement (HANSA and AlphaBay). But others have popped up. While writing this chapter, I took 15 minutes to search for dark web markets and it was trivial to find multiple sites that sell drugs, stolen data, firearms, and more. Methamphetamine, cocaine, heroin, all for sale. There is far more available on these dark web markets. Jihad training sites, instructions on how to make explosives, hacking services, places to buy and sell malware....

While some prominent markets have been taken down by law enforcement, others remain in operation. As of this writing, some of the markets with the most activity include:

- **The Dream Market:** http://lchudifyeqm4ldjj.onion
- **Silk Road 3:** http://silkroad7rn2puhj.onion/
- **Valhalla:** http://silkkitiehdg5mug.onion
- **Grams:** http://grams7enufi7jmdl.onion
- **Pushing Taboo:** http://pushingtabu7itqj.onion/
- **Wall Street:** http://wallstyzijhkrvmj.onion/signup?ref=276
- **T Chka Market:** http://pointgg344ghbo2s.onion

Search engines and starting points:

- **http://xmh57jrzrnw6insl.onion/:** Torch, a search engine
- **https://hss3uro2hsxfogfq.onion.to:** A search engine
- **http://dirnxxdraygbifgc.onion:** OnionDir, a directory of dark websites
- **http://kbhpodhnfxl3clb4.onion:** Tor Search, a search engine
- **http://ndj6p3asftxboa7j.onion:** Tor Find, a search engine
- **linkzbg4nwodgic.onion:** Just basic link lists
- **jdpskjmg5kk4urv.onion:** Dark web links

You should be aware that these sites come and go. Some may not be up and running by the time you read this. Before you begin surfing the dark web, you should be aware that it is inherently dangerous. Certainly, the traditional web has its share of scams, malware, and other dangers. But the dark web is simply awash in such dangers. Before you begin searching the dark web, I strongly advise you to take the following safety measures.

Many websites have spyware, viruses, and other malware. Therefore, one must establish a specific environment for dark web activities. That environment should be a virtual machine that is completely isolated from the host operating system. That means, no sharing of the clipboard or folders. The virtual machine is preferably of a different operating system than the host, making crossing the VM barrier even more difficult. And finally, that VM should only be used for the dark web activities, and for no other purpose. That way, if it should become infected with spyware, the person controlling the spyware will not gain information about the investigator’s real identity.

It is also possible to penetration test a dark web market. As with traditional penetration testing, this begins with finding vulnerabilities in the dark web market site. Fortunately, tools are emerging that assist in this endeavor. The website ichidan (http://ichidanv34wrx7m7.onion) tracks vulnerabilities in dark web sites. This site operates similarly to the traditional Internet site shodan.io, which is a search engine for vulnerabilities in normal websites. Figure 17-3 shows ichidan used to search for default values on any dark website.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_380_0.png)

FIGURE 17-3 ichidan Search.

The dark web should be part of your assessment of a given organization’s security. If that company’s data is for sale on the dark web, there has already been some breach of the company’s security. In project 2 at the end of the chapter, you will actually see exactly how to connect to the dark web and conduct a search.

## Certification and Training

Chapter 1, “Introduction to Penetration Testing,” briefly discussed industry certifications. In this chapter we will delve deeper into options for training, certifications, education, and more. As you are reading a book on penetration testing, clearly you have a desire to learn. You may even be reading this book as part of some class. However, you have entered a field where constant learning is a must. You will never know everything there is to know, and you must constantly be learning more. How do you address this issue? Moreover, do you know enough to start a career in penetration testing? In this section I will answer these questions.

Let us begin with examining the requisite knowledge to be a penetration tester. Periodically, I see people advocate that formal education is irrelevant for penetration testing, or for cyber security in general. And such people will point to someone with a completely irrelevant degree (such as history, for example) or no degree at all, who happens to be doing well in this career. My experience does not support this.

In general, those without any solid computer science background may have a career in cyber security, even penetration testing, but will have significant gaps in their knowledge. And these are gaps that would have been filled with some solid computer education. To be successful in cyber security, you need a working knowledge of how networks operate, computer operating systems, and some programming language, just to have a basic understanding of cyber security. For penetration testing, even more so.

The fact is that to be truly effective at security requires a broader skill set than most other areas of IT. If you are an Oracle DBA, you really only need to know Oracle. If you are a driver programmer, then you need to really know C, and probably Assembly. But if you are in security, you need to have a working knowledge of networking, at least one or two programming languages, databases, operating systems, etc., as well as security-specific knowledge such as standards, procedures, pen testing techniques, etc. And frankly, all too many security professionals just don’t have that diverse knowledge. This is a very demanding profession that will require a very high standard. To use as an analogy medical doctors, cyber security is not like being a family practitioner, podiatrist, etc. To do it right is more akin to specialized surgical disciplines. And those require more training (both initially and ongoing continuing education).

There are certainly people in cyber security (and in IT in general) without relevant degrees. However, having done this for about 30 years, my experience has been that these people fall into one of two categories:

- The serious “computer nerd” who might not have a computer degree, but has been tinkering with computers, coding, etc. since childhood. This person may not have a computer degree, but has read more computer science books than they would have in obtaining three degrees. Their lack of formal education is compensated with a lifetime of delving into the topic.
- The second group are simply not as good as they think they are. I frequently meet people with irrelevant degrees or no degree at all, but with 10+ years of experience. Many of those are very good at a very narrow scope of skills. They may know Java programming very well, but don’t really understand CPU architecture, algorithm design, data structures, and other topics they would have understood with formal training.
