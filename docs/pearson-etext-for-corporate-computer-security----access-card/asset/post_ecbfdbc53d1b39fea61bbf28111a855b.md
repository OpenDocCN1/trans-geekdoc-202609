
## AJAX MANIPULATION

Ajax, which is short for Asynchronous JavaScript XML, uses multiple technologies to create dynamic client-side applications. Using Ajax is advantageous because it allows local webpages to dynamically change without having to interact with the server each time a change is made. However, the dynamic nature of Ajax makes it susceptible to malicious code injection, altered XML, manipulation of client-side validations, and so on.

## TRAINING IN SECURE COMPUTING

Validating user input can only thwart some attacks. Programmers who create custom programs need to be trained in secure programming in general and for their particular programming language and application.

Explaining how each of these numerous flaws work and how to protect against them would fill several textbooks. Some of the more common flaws in web-based applications include improper session management, passing invalid parameters, and concurrency errors.

There are training platforms that allow programmers and systems administrators to learn more about how these flaws can be exploited. OWASP-WebGoat (OWASP.org) and Foundstone’s HackMe series (Foundstone.com) are both designed to provide a safe training environment with known application weaknesses.

## Test Your Understanding

- 6. a. What is a login screen bypass attack?
- b. What is a cross-site scripting (XSS) attack?
- c. What is a SQL injection attack?
- d. What attitude should programmers have about user input?
- e. What training should programmers who do custom programming have?

## In the News

### Credential-Stuffing Banks

In 2019 Akamai Technologies released its latest State of the Internet Report detailing some of the most damaging Internet attacks. Akamai noted that it saw more than 3.5 billion credential-stuffing attacks in the prior year and a half. Credential stuffing is when an attacker tries to gain access to user accounts by logging in with stolen usernames and passwords. Login credentials are either stolen from companies or gathered directly from users via phishing scams. Akamai saw more than 197,000 domains associated with known phishing scams targeting consumers.

The report goes on to note that the majority of credential stuffing attacks were focused on the financial services industry. It seems the most profitable way crooks are making money today is to steal login credentials from users via phishing scams and then launch a credential-stuffing attack against large financial institutions. Consumers and financial institutions need to be aware of this trend and take steps to actively protect themselves.

### Airbus and Boeing Software Flaws

In 2019 Airbus notified owners of its Airbus A350 planes that their internal systems must be hard rebooted before they reach 149 hours of continuous use.^2 If they’re not rebooted, certain internal avionics systems will stop working. Airbus A350s operating before 2017 were experiencing this flaw, yet the flaw wasn’t disclosed until 2019. Updates to the system have resolved this issue.

But Airbus isn’t alone. In 2019 Boeing experienced a software flaw that affected the angle-of-attack alert system that may have been involved in a few high-profile plane crashes.^3 The software flaw has led to the cancellation of billions of dollars’ worth of orders for Boeing’s 737 Max.

Authorities worry that hackers could take advantage of these flaws and intentionally cause planes to crash. That almost happened in 2015 when security researcher Chris Roberts of One World Labs hacked into a commercial airliner in flight.^4 Roberts issued commands causing the plane to climb and fly sideways. During questioning by the FBI, Roberts said he had hacked into planes 15 to 20 times.

### Largest Bank Card Theft

In 2018 Russian hackers Vladimir Drinkman and Dmitry Smilianets were sentenced to prison for organizing the theft of more than 160 million bank cards.^5 The pair were part of a larger hacker group that specialized in SQL injection attacks to steal information. The group targeted well-known companies like 7-Eleven, NASDAQ, Wet Seal, Heartland, and JetBlue. Federal investigators weren’t able to estimate the damages done by the hacking group, but they estimated losses to just *three* of the victims were over $300 million.

Drinkman and Smilianets were arrested by Dutch authorities and extradited to the United States. Drinkman received a 12-year sentence, and Smilianets received a 4 1/2-year sentence. The remaining three conspirators—Alexandr Kalinin, Roman Kotov, and Mikhail Rytikov—are still being sought by authorities.

### Bug Bounties

In 2018 researcher Artem Moskowsky found a flaw in a developer portal for Steam that allowed him to download game licenses and play pirated games. More specifically, Moskowsky found that if he injected a random string of characters into an API request he could get a large number of software license keys for any game.^6 In one instance he got 36,000 keys from a single modified request. Each key is worth about $10. Moskowsky reported the vulnerability and was rewarded with a $20,000 bug bounty from Valve. Paying bug bounties is much cheaper and easier than responding to the loss of tens of millions of dollars’ worth of intellectual property. Hackers love bug bounties because they get paid and don’t have to break the law. Companies love them because they can resolve security issues fairly inexpensively.

^2 Gareth Corfield, “Airbus A350 Software Bug Forces Airlines to Turn Planes Off and On Every 149 Hours,” *The Register*, July 25, 2019. www.theregister.co.uk/2019/07/25/a350_power_cycle_software_bug_149_hours.

^3 Benjamin Goggin, “Boeing Reportedly Knew of the Software Error on the 737 Max for a Year before Telling Airlines and Regulators,” *Business Insider*, May 5, 2019. www.businessinsider.com/boeing-knew-737-max-software-error-year-before-telling-faa-2019-5.

^4 Elizabeth Weise, “Computer Expert Hacked Into Plane and Made It Briefly Fly Sideways, According to FBI,” *The Independent*, May 17, 2015. www.independent.co.uk/news/world/americas/computer-expert-hacks-into-plane-and-makes-it-fly-sideways-according-to-fbi-10256145.html.

^5 Iain Thomson, “Russians behind Bars in US after Nicking $300m+ in Credit-Card Hacks,” *The Register*, February 16, 2018. www.theregister.co.uk/2018/02/16/two_russians_jailed_credit_card_hacks.

^6 Shaun Nichols, “I Found a Security Hole in Steam That Gave Me Every Game’s License Keys and All I Got Was This... Oh Nice: $20,000,” *The Register*, November 9, 2018. www.theregister.co.uk/2018/11/09/valve_steam_key_vulnerability.

Webserver programs, as Figure 8-11 shows, often have components that come from different companies. For instance, the PHP application development software is built into many webservers. PHP vulnerabilities have been found in software from *almost all* webserver vendors.

### E-COMMERCE SERVICE
We will use the term **e-commerce service** to refer to the additional software needed for buying and selling, including online catalogs, shopping carts, checkout functions, connections to back-end databases within the firm, and links to outside organizations, such as banks.

> We will use the term *e-commerce* to refer to the additional software needed for buying and selling.

### EXTERNAL ACCESS
An e-commerce server needs to have network access to a number of systems external to itself, including servers within firms (for order entry, accounting, shipping, etc.) and servers outside the firm in merchant banks and companies that check credit card numbers for validity. The webmaster or e-commerce administrator often has no control over the security of other systems.

## Figure 8-12 Microsoft IIS 10 Webserver

![](img/073342643701cc54eb7875c41ab92ef2_409_0.png)

![](img/073342643701cc54eb7875c41ab92ef2_409_1.png)

## Figure 8-13 WWW and E-commerce (Study Figure)

### CUSTOM PROGRAMS
Many companies that use e-commerce software write their own programs to supplement the capabilities of the packaged software they purchase. As noted earlier in this chapter, most firms do a poor job of overseeing the development of these custom programs. Consequently, attackers often can exploit vulnerabilities in custom programs or, even more insidiously, write their own custom programs that they can execute on the victim server to aid in their attacks.

Many firms believe that attackers will not know their custom software and so will have a difficult time hacking these programs. However, most programming languages produce programs that have common security failure modes that are well known by hackers. We saw an example of this earlier in the chapter, when we looked at cross-site scripting. The attacker only had to know that the site reflected user input. To learn this, the attacker only had to send input and see if it was reflected.

## Test Your Understanding

- 8.
- a. Distinguish between WWW service and e-commerce service.
- b. What kinds of external access are needed for e-commerce?
- c. Does the webmaster or e-commerce administrator have control over the security of other servers?
- d. Why are custom programs especially vulnerable?

## Some Webserver Attacks

How do attackers attack webservers? In this section, we will look at a number of web-server attacks.

### WEBSITE DEFACEMENT
A common attack is **website defacement**—taking over a computer and putting up a hacker-produced page instead of the normal home page. Although this generally is only a nuisance, it can be much worse. For instance, after a fatal airplane crash, hackers defaced the ValuJet website with the statement “So we killed a few people.” Even worse, hackers sometimes install “out of business” home pages to get customers to go away and stay away.

### BUFFER OVERFLOW ATTACK TO LAUNCH A COMMAND SHELL
Earlier in this chapter, we discussed the IIS IPP buffer overflow vulnerability and the jill.c program used to exploit the vulnerability. We noted that the attacker gets a command shell and strong *(system)* privileges. IIS has been subject to many other buffer overflow attacks with equally devastating impacts. So have other webserver programs.

### DIRECTORY TRAVERSAL ATTACK
Sometimes, the attacker knows that a certain sensitive file, such as a password file, normally is stored in a particular directory under a particular name. The attacker would like to download many of these sensitive files.

When users send a request for a file to be downloaded, the “root” is really a particular directory owned by the webserver. We will call this directory the **WWW root**. Figure 8-15 illustrates the WWW root. Here, the WWW root is one level down from the computer’s true root. If the user types the path */Projects/Bak.doc*, the request does not go to the server’s root and then go one level down to a *Projects* directory. Instead, it starts at the WWW root directory and goes one level down to the *Projects* subdirectory. It then retrieves the *Bak.doc* file stored in that directory.
