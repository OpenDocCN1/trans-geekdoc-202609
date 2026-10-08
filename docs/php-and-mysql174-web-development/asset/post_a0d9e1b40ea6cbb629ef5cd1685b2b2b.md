
# Compromised Server

Although the effects of a compromised server can include the effects of many of the threats previously listed, it is still worth noting that sometimes the goal of invaders is to gain access to our system, most often as a super user (administrator on Windows-based systems and root on Unix-like systems). With this, they have nearly free rein over the compromised computer and can execute any program they want, shut the computer off, or install software.

We want to be particularly vigilant against this type of attack because one of the first things attackers are likely to do after they have compromised a server is to cover their tracks to hide the evidence.

# Reducing the Risks

Protecting against server compromise requires an approach called defense-in-depth, which we will discuss in more detail in Chapter 15. In summary, this means thinking about all the possible things that could go wrong in different aspects of a system, and putting in layers of protection for each aspect.

One mitigation strategy worth mentioning here is the use of an Intrusion Detection System (IDS) such as Snort. These are used to monitor and alert for network traffic that looks like an attack.

# Repudiation

The final risk we will consider is reputation. Repudiation occurs when a party involved in a transaction denies having taken part. E-commerce examples might include a person ordering goods off a website and denying having authorized the charge on their credit card, or a person agreeing to something in it and claiming that somebody forged the email.

Ideally, financial transactions should provide the peace of mind of nonrepudiation to both parties. Neither party could deny their part in a transaction, or, more precisely, both parties could conclusively prove the actions of the other to a third party, such as a court. In practice, this rarely happens.

# Reducing the Risk

Authentication provides some surety about whom you are dealing with. If issued by a trusted organization, digital certificates of authentication can provide greater confidence. The certificate authentication system has some flaws, but it's the current standard.

Messages sent by each party also need to be tamperproof. There is not much value in being able to demonstrate that Corp Ltd sent you a message if you cannot demonstrate that what you received was exactly what the company sent. As mentioned previously, signing or encrypting messages makes them difficult to surreptitiously alter.

For transactions between parties with an ongoing relationship, digital certificates together with either encrypted or signed communications are an effective way of limiting reputation.

# Understanding Who We're Dealing With 339

For one-off transactions, such as the initial contact between a web application and a stranger bearing a credit card, they are not so practical.

Web companies need to provide proof of their identity and a few hundred dollars to a certifying authority as Symantec (http://www.symantec.com/), Thawte (http://www.thawte.com/), or Comodo (http://www.comodo.com/) to assure visitors of the company's bona fides. That same company be willing to turn away every customer who was not willing to do the same to prove his or her identity? For small transactions, merchants are generally willing to accept a certain level of fraud or predation risk rather than turn away business.

# Understanding Who We're Dealing With

Although we might instinctively classify all who cause security problems as bad or malicious people intent on causing harm, there are often other actors in this arena who are unwitting participants and might not appreciate being called.

# Attackers and Crackers

The most obvious and famous group are what we call crackers or attackers. We resist the urge to call them hackers, because this is annoying to real hackers, most of whom are perfectly honest and well-intentioned programmers. Crackers attempt, under all sorts of motivations, find weaknesses and work their way to achieve these goals. They can be driven by greed, if they are after financial information or credit card numbers; driven by money, if they are being paid by a competitive firm to get information from their systems; or can simply be talented individuals looking for the thrill of breaking into yet another system. Although they present a serious threat to us, it is a mistake to focus all on their efforts.

# Unwitting Users of Infected Machines

In addition to crackers, we have to worry about a large number of other people. With all the weaknesses and security flaws in many pieces of modern software, an alarming percentage of computers are infected with software that performs all of dubious tasks. Some users of your internal corporate network might have this software on their machines, and that software might be attacking your server without those users realizing it.

# Disgruntled Employees

Company employees constitute another group you might have to worry about. These employees, for reason or another, are intent on causing harm to the company for they work. Whatever the motivation, they might attempt to become amateur crackers themselves, or acquire tools from external sources by which they can probe and attack servers from inside the corporate network. If we secure ourselves well from the outside world, but leave ourselves completely exposed internally, we are not secure. This is a good argument for implementing what is known as a demilitarized zone (DMZ), which we will cover in the next chapter.

# Hardware Thieves

A security threat you might not think to protect yourself against is somebody simply walking into the server room, unplugging a piece of equipment, and walking out of the building with it. You might find surprised how easy it is to walk into a great corporate offices and just stroll around without suspecting anything. Walking into the right room at the right time find themselves with a shiny new server, along with hard disks full of sensitive data.

# Ourselves

As unpleasant as it may be to hear, one of the biggest headaches we might have for the security of our systems is ourselves and the code we write. If we write sloppy code and do not pay any attention to testing and verifying the security of our system, we have given malicious users a huge hand in their attempts to compromise our system.

If you are going to do it, do it properly. The Internet is particularly unforgiving to those prone to carelessness or laziness. The hardest part of sticking to this mantra is convincing a boss or financial decision maker that is worthwhile. A few minutes teaching them about the negative effects (including those against the bottom line) of security lapses should be enough to convince them that the extra effort will be worthwhile in a world where your data is worth everything.

# Next

A good resource for learning more about the threats to your web application is the Open Web Application Security Project (OWASP). Each year they publish a list of the top 10 threats to web applications, as well as a wide range of excellent ebooks and other resources on web security. You can find them at https://www.owasp.org.

In Chapter 15, "Building a Secure Web Application," we will look at how to protect against the threats we discussed in this chapter.

# 15
Building a Secure Web Application

In this chapter we continue the task of looking at application security, looking at the broader theme of securing our entire web application. Indeed, every single part of our web applications will need to be secured from possible misuse (accidental or intentional), and we will want to develop some strategies for developing our application that will help us stay secure.

Key topics covered in this chapter include

- Strategies for dealing with security
- Securing your code
- Securing your web server and PHP
- Database server security
- Protecting the network
- Disaster planning
