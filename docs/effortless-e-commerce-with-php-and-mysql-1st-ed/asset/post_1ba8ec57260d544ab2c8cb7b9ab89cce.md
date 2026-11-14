
## Maximum Security Isn't the Goal

Again, this may sound blasphemous, but it's really not. You have to first accept that security comes at a cost. Making something—pretty much anything—more secure requires more time and money. Also, anything that's more secure is inherently less usable and, in terms of computers, slower (Figure 2.2).

![](img/4f47e47c67bd619ac73250f11c9fc7ce_44_0.png)

> **tip**
> The success of a site will increase its risks, as the extra attention will make it a bigger target for hackers.

Returning to my car analogy, if you live in a city, you likely lock the car when you drive it somewhere and park. But when you park it in your garage, you probably don't lock it. The same might be true if you live in a small town or if your car is a total beater. In some situations, maybe you use a secondary anti-theft device, like a steering wheel lock. What you're doing with your car, consciously or not, is adjusting the security measures in place based upon the perceived level of risk and the potential loss (for example, an expensive car versus a cheap one).

This is true of Web sites, as well: Different types of sites require different levels of security. A site that lists my favorite books is at a different point on the security spectrum than one that stores user information. Even that is on a less critical plateau than a site that handles credit cards. Even beyond that high-security level, there are sites for online banking, sensitive government and/or military data, and so forth (Figure 2.3).

![](img/4f47e47c67bd619ac73250f11c9fc7ce_44_1.png)

The goal, then, isn't to implement the highest level of security but rather the _highest level of security that's appropriate for the site_. Here are two concrete examples of what I mean:

You may already know that the Secure Sockets Layer (SSL) is an essential part of the e-commerce system. SSL provides the first line of defense for protecting user-submitted information; when the time comes to take the customer's credit card, SSL must be used. But this doesn't mean that SSL must be used for every page on your site. SSL puts a strain on the server, and only a fraction of SSL requests can be handled simultaneously compared to non-SSL requests. As a compromise between security and performance, you may choose to only use SSL for the checkout process, and use a non-SSL connection for the bulk of the site.

As another example, a shared host is going to be less secure than a dedicated host simply because more people have access to, and more software is running on, the server. On the other hand, a shared host will cost a tenth or less of what a dedicated host costs. You can increase the security by purchasing a more expensive hosting plan, but that may not be necessary, let alone prudent.

All this being said, I don't want you thinking that I'm cavalier about security or that you should be. In this chapter, you'll learn the fundamentals for creating a secure Web site, but it's not reasonable to think that your site has to be secure to the nth degree. There are many baseline recommendations—in terms of code and server environments—that you should ideally implement for any site. But you'll be presented with plenty of choices for which you must weigh all the pros and cons before coming to a decision. The goal is to hit the appropriate mark on the security spectrum for the given situation (as in Figure 2.3). Then, give your site a nudge just a wee bit to the right on that spectrum, just to be safe.

- **tip**
- When making security decisions, always err on the side of being too overprotective.

### Security for Customers

E-commerce sites and Web sites in general have a client-server relationship: two parties equally participating in an event. There are two sides to security, as well: one you implement as the site developer and/or server administrator and one the customer is aware of. Now let's take a couple of pages to think about security from the customer's perspective.

- **tip**
- The success of an e-commerce site partly depends upon a customer's comfort in spending money there.

There's an old expression that says cleanliness is next to godliness. My house wouldn't suggest that I live by that expression, but it leads me to an analogy I have for Web site security:

> Security is Next to Godliness.

Think of security the way you might think about cleanliness. Say you go to eat at a restaurant ... the restaurant may or may not *look* clean, and it may or may not *be* clean. But if the restaurant doesn't look clean, then it probably isn't actually clean, and you don't want to eat there. The same goes for a Web site's security: If it doesn't give the appearance of being secure, it probably isn't secure, and potential customers won't want to use the site (and shouldn't). So how does a site look secure to the lay user? It...

- Is professional in appearance
- Is honest and transparent with respect to what the business is, what its policies are, how customer information will be used, and so on
- Uses SSL
- Doesn't do anything that may make the customer feel the site isn't secure

> > **tip**
> > Having friends and family test your site is a good way to get feedback on potentially confusing or problematic parts.

This last quality is really the most important, as the common person may not really know the difference between a secure-looking and unsecure-looking site. A successful e-commerce site gives customers every reason to complete their sale and absolutely no reason not to. If a customer goes to a site and sees technical error messages, alerts from their browser (for example, because of poor JavaScript or improper use of SSL), and so forth, they'll likely take their business elsewhere. If the Web site does something that makes the customer say “Huh?” think of it like seeing a rodent scurry across the restaurant floor: It's time for the customer to go.

The second part of this analogy is that while it's important for a restaurant to look clean (so people will eat there), it's more important that it's actually clean (so that patrons don't get sick, so that the inspector doesn't shut it down, and so on). Your Web site must actually be secure, so that nothing bad can happen to the customers or your client.

> > **tip**
> > If you're creating a site for a client, put a plan in place so that someone continues to maintain the site's security after you're finished with the project.

The final reason I believe this analogy works is that it also supports the two maxims I already put forth. Security, like cleanliness, isn't an absolute and the amount of effort you put into it should depend upon the situation. The place where a restaurant keeps its garbage doesn't need to be that clean, but the kitchen sure does. Maybe you're the kind of person that would thoroughly clean monthly, weekly, or daily. Maybe you're the kind that will take cleaning to the disinfecting level. There's no right answer in these situations: There's better and there's worse, and there's what's right for you and your situation. The same goes for security. Most importantly, just because you cleaned today, doesn't mean it will stay clean forever. And the Web site that went live today without any issues could become vulnerable tomorrow, even if that's through no fault of your own.

## PCI REQUIREMENTS

In Chapter 1, "Getting Started," I mention that you'll need to be aware of PCI compliance. Compliance means abiding by all twelve requirements outlined in the PCI DSS. Depending upon your level of involvement in the e-commerce project, some of these may not be applicable to you personally, but you should still be aware of them and pass them along to those that are responsible.

Taken verbatim from www.pcisecuritystandards.org, the requirements are:

### Build and Maintain a Secure Network

- Requirement 1: Install and maintain a firewall configuration to protect cardholder data.
- Requirement 2: Do not use vendor-supplied defaults for system passwords and other security parameters.

### Protect Cardholder Data

- Requirement 3: Protect stored cardholder data.
- Requirement 4: Encrypt transmission of cardholder data across open, public networks.

### Maintain a Vulnerability Management Program

- Requirement 5: Use and regularly update anti-virus software.
- Requirement 6: Develop and maintain secure systems and applications.

### Implement Strong Access Control Measures

- Requirement 7: Restrict access to cardholder data by business need-to-know.
- Requirement 8: Assign a unique ID to each person with computer access.
- Requirement 9: Restrict physical access to cardholder data.

### Regularly Monitor and Test Networks

- Requirement 10: Track and monitor all access to network resources and cardholder data.
- Requirement 11: Regularly test security systems and processes.

### Maintain an Information Security Policy

- Requirement 12: Maintain a policy that addresses information security.

If you go to the PCI Web site, you can download a 70-plus-page PDF that explains each of these regulations in more detail. The document also discusses how to test each condition and provides a worksheet to annotate your results. You should read this PDF at some point, but I want to add a few notes of my own here.

> Extra precautions apply if wireless technology will be used on your business's internal network.

> Depending upon the level of PCI compliance that applies to your business, you may be required to perform annual validation tests.
