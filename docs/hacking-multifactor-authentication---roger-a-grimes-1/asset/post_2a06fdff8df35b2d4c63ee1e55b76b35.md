
# Summary

As you can read there are a ton of different authentication options ranging from a person's physical presence and voice (and other biometric factors) to advanced MFA solutions involving external devices or cellphones, and everything in between. We covered the following categories: personal recognition, knowledge-based authentication, password managers, proxies, cryptography, hardware tokens, phone-based authentication, biometrics, federated solutions, contextual/adaptive, and radio-paper-based solutions. If I missed your favorite authentication solution type, I apologize for advance. I covered every type I could remember, but I'm only human. Picking the right one for the authentication scenario is key to maintaining the right amount of security versus usability, which is discussed in the next chapter.

# Usability vs. Security

Security has always been a struggle between usability and safety, and that struggle is definitely involved in deciding which MFA solution to use. Admins and IT are moving to MFA precisely to improve security. Many users really don't want the best security when it impacts usability. This chapter explores many of the main points of usability versus security. It contains lots of “hard truths” that can be surprising for some readers to learn. It might seem a bit out of place for a book dedicated to MFA.

This chapter will start with a brief discussion of usability, and more detail on usability will be discussed in Chapter 23, “Selecting the Right MFA Solution.” The bulk of this chapter is dedicated to the value of usability when it's competing with security.

# What Does Usability Mean?

MFA must be sufficiently user-friendly that people won't mind using it and that management feels they can require. It must work with the organization's critical applications and fit within the culture. Not all MFA solutions meet both criteria. No MFA solution works with everything. Organizations always have to pick which critical applications will end up protected with MFA.

And organizational cultures seem more inclined to particular types of MFA. For example, an organization whose employees already use physical building entries are more likely to be open to smartcards. Companies that are “Google shops” are more likely to be open to Google keys and/or the Google Authenticator timebased-one-password (TOTP) app. Organizations with high-end security needs are probably better candidates for biometrics, since employees (mistakenly) relate biometrics to strong security. Companies with lots of remote employees are probably more open to hardware keys, like Fast Identity Online (FIDO) devices, or phone apps.

# Hacking Multifactor Authentication

users is required. Troubleshooting costs need to be considered. How much will it cost to replace or reinstall the MFA solution if it breaks for a particular user? How will tech support cost it? It is not unusual for various MFA support calls to cost the supporting entity upward of $200 per call in both labor and relation support costs (replacement tokens, help software training, corporate space, overhead, etc.). The organization must create supporting policies, training documentation, and recovery steps ahead of time.

Training the ability of users to understand and correctly use MFA solutions should not be overstated, especially as your end-user enterprises get larger, more global, and more diverse. A fantastic representative presentation to see or hear about MFA training challenges is Studies of 2FA's "Why Johnny Can't Use 2FA and How We Can Change" (www.rsaconfer.com/industry-topics/of-2fa-why-johnny-cant-use-2fa-and-how-we-can-change-that). You can download the slide deck here: published-layoneevents.com/rsaus19-sessionsFiles/13259/IDY-TOT-Studies-of-2FA-Why-Johnny-Can't-use-2FA-and-How-We-Can-Change-pdf. If you are interested in security vulnerability, this presentation and slide deck, including notes, is worth your time.

The talk was to a university study to see how well regular ends could understand and use instructions for basic MFA solutions. In their study, the researchers participated people and popular simple MFA. The users had to plug the device into their computer's USB port and press one button to activate the device. Each user was given instructions on how to operate and use their device. Plugging something to a USB port and push a button. How could that be?

The failure rate was seventy percent—a 70 percent failure rate for that simple. Many of the participants plugged the device upside down (not unthinkable with a USB device), having either the device or the port. Another set of users used their finger over instead of simply pressing. Many times the device was not working at all, but the users thought they had successfully performed all actions and were using an MFA device. Just as many had successfully installed it but were not sure and didn't use.

After the study, the researchers told all participants that they could keep their MFA devices and use them. They waited a month and contacted all the participants to see if they decided to keep their device. Not a single participant was still using! Worse, many participants had given their device, which was tied to their identity, to other people or had placed the device in a lost-and-found box for others to use. They seemed unaware that any relishing their device into a computer and pressing a button would enable them to successfully authenticate as them.

In a similar study (www.blackhat.com/html/webcast/11292018-two-factor-authentication-usable-or-not.html), researchers wanted to see how many people could enroll in and use a popular 2FA token is what the first study did not consider. They found the same thing: a large percentage of users unable to properly use MFA devices and who were able to use them but didn't. Here's our presentation out: 1.blackhat.com/

# Chapter 4 Usability vs. Security

Here are other MFA studies in you are interested:

- www.usenix.org/system/files/soups2019-reece.pdf
- www.archive.ece.cmu.edu/~bauer/papers/2018/chi2018-2fa.pdf
- ueaeprints.ua.ac.uk/eprint/61540/1/MahaAltob.pdf
- scholarsarchive.byu.edu/cgi/viewcontent.cgi?article=7869&context=etd

The studies communicate two things. No matter how you think the selected MFA solution is, there is a certain percentage of users who will struggle with, at least initially. Second, and just as important, users really not like to use MFA solutions even when they are free. And that leads us to the next and main part of chapter.

# We Don't Really Want the Best Security

Every computer security person understands the challenge of implementing good security controls without annoying users or making them inefficient in their job or tasks. Computer security experts are always trying to improve security and lower cybersecurity risk, and sometimes (especially new people to the field) can get up in thinking that making security is the only goal that matters. That's from the case.

Any experienced security person will tell you that if you leave it to most ends they would want little to no security if it actually makes them a double adding thing that slows down in the slightest. Many people want the least amount of "friction" to the point that they would prefer to no security if it means slowing down from what they want to do. Well, they want everyone to have what's needed as security is needed, but they feel that they, themselves, do really need much "cumbersome and onerous" computer security controls. They feel they know what they are doing and that security only slows them down.

They reluctantly put up with what security controls management tells them that they have to. They want the bare controls that they perform for their job relatively safely and effectively, and they don't want those. What do they have because someone else higher up the chain said they have to. Until something.

It's not like computer security professionals can design secure solutions that prevent most to all cybersecurity incidents. Most of us can design computer security controls that would stop hackers and malware. It is designing them without an added burden to end users and keeping management's support that's the tricky part.
