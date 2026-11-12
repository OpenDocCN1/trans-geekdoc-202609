
- Rogue URL Tricks 315
- Summary 334
- **Chapter 14** Fighting Spear Phishing 335
- Background 335
- Spear Phishing Examples 337
- How to Defend Against Spear Phishing 345
- Summary 347
- **Chapter 15** Forensically Examining Emails 349
- Why Investigate? 349
- Why You Should Not Investigate 350
- How to Investigate 351
- Examining Emails 352
- Clicking on Links and Running Malware 373
- Submit Links and File Attachments to AV 374
- The Preponderance of Evidence 375
- A Real-World Forensic Investigation Example 376
- Summary 378
- **Chapter 16** Miscellaneous Hints and Tricks 379
- First-Time Firing Offense 379
- Text-Only Email 381
- Memory Issues 382
- SAT Counselor 383
- Annual SAT User Conference 384
- Voice-Call Tests 385
- Credential Searches 385
- Dark Web Searches 386
- Social Engineering Penetration Tests 386
- Ransomware Recovery 387
- Patch, Patch, Patch 387
- CISA Cybersecurity Awareness Program 388
- Passkeys 388
- Avoid Controversial Simulated Phishing Subjects 389
- Practice and Teach Mindfulness 392
- Must Have Mindfulness Reading 393
- Summary 393

## Chapter 17 Improving Your Security Culture 395
### What Is a Security Culture? 396
### Seven Dimensions of a Security Culture 397
### Improving Security Culture 401
### Other Resources 404
### Summary 404
## Conclusion 405
## Acknowledgments 407
## About the Author 411
## Index 413

## Introduction

Social engineering has been around since the beginning of humanity, and phishing has been around at least since the beginning of networked computers. I can remember my first brush with social engineering via computers in 1987. This was before most people had even heard of something called the Internet and before most people had personal computers. Many of us early adopters were on a precursor of the Internet called the FIDONet. Back in those days, you would use a 300 or 1200 BAUD or BPS (Bits Per Second) dial-up analog modem to call your local BBS (Bulletin Board System). This system would use a crude “store-and-forward” technology that would transmit and receive messages and files around the world in a day or so. We thought it all was pretty cutting-edge.

On one of the BBSs, I came across a downloadable text file named “How to Get a Free HST Modem.” HST modems, made by US Robotics, were the fastest and best modems available at the time. They ran at an incredible 9600 BPS. They were expensive enough that only a few lucky, monied, people had them. They were mostly only used by Fortune 500 companies and well-funded universities. This file promised to tell anyone who read it how to obtain a free one. It was too enticing to pass up.

I opened up the file and inside it contained only text that said, “Steal One!” “Well, that was disappointing!,” I thought. Then the very next keyboard key I pressed formatted (i.e., permanently erased) my hard drive and rendered my computer useless. Well, at least until I reinstalled the operating system and redid everything all over again. I lost all files.

It turns out the file was something called an “ansi-bomb.” It was a malicious file that took advantage of a feature of a legitimate operating system file called ansi.sys. Ansi.sys was a part of Microsoft’s DOS operating system, which most of us ran at the time. Ansi.sys was an optional file that allowed users to have extended, “cool,” features for their screen and keyboard, such as displaying special graphics and characters on your screen. It also allowed savvy users to map sequences of commands to a single key on their keyboard. It was meant to allow people to create “macros”—an automated shortcut that triggered a longer sequence of key presses. You could hit one or two keys and automate what would otherwise be a bunch of other key presses. Some malicious jerk had created a malicious file that instructed ansi.sys to map all the keys on the user’s keyboard to format the user’s hard drive when the next key was pressed.

It was a lesson learned.

There are malicious people in the world who want to harm other innocent people for no other reason than they can. Not everyone in the world is friendly and helpful, especially to strangers.

Now, the impact of social engineering and phishing on cybercrime has been driven home to me tens of thousands of times during my career. Today, nearly everyone understands that social engineering and phishing are responsible for more cybercrime than any other single initial root cause method. No other root cause of hacking is even close. But just a decade ago, even though it was true then, it wasn’t as well known by all cybersecurity defenders. I think everyone knew social engineering and phishing was a problem, but few knew exactly how big of a problem it was. Few defenders knew it was the number one problem by far. Even I didn’t.

I worked as a Principal Security Architect for Microsoft Corporation for nearly 11 years, from 2007 to 2018. For much of that time, I did security reviews for customers and installed Public Key Infrastructures (PKI) and advanced security defense systems. I was promoted, usually well-liked by clients, and always installed systems on time and on budget, which isn’t so normal in the computer industry. For years I felt like I was greatly helping to protect my customers.

Then I realized that *every single* customer I had, no matter what defenses we installed, was still falling prey to hackers and malware. This was despite installing the best computer security defense systems possible. Why? It was almost always due to social engineering (and, secondarily, unpatched software). Even though all my customers were spending hundreds of thousands to millions of dollars to protect themselves using the most advanced systems the industry could imagine and deliver, what was taking them down was the same things that were most often taking down companies since the beginning of computers—social engineering. And usually, phishing.

That realization occurred to me in about 2016. It made me depressed. Instead of seeing myself as part of the solution, I realized I wasn’t really helping my clients to avoid hackers and malware. What I was doing was more smoke and mirrors. I was wasting their time and money. But it wasn’t like I was alone. Most computer security companies and consultants did what I did, which was concentrating on everything but defeating social engineering and phishing, even though they were clearly the biggest problem by far. Still, it bothered me tremendously.

I eventually wrote the first edition of a book about my realization, *A Data-Driven Defense: A Way to Improve Any Computer Defense* (www.amazon.com/Data-Driven-Computer-Defense-Should-Using/dp/B0BR9KS3ZF) in 2018. The book sold over 50,000 copies (over three editions), and its premise—social engineering is most companies’ biggest cybersecurity threat—led me to work for my current employer, KnowBe4. The CEO of KnowBe4, Stu Sjouwerman, was one of the first people to read my book and understood its value in not only recognizing the importance of fighting phishing and social engineering but also in creating an effective cybersecurity defense using data. In April 2018, Stu offered me a job and I accepted. I was delighted. Not only was I going to start working for a leading firm in security awareness training, which is one of the best ways to fight social engineering and phishing, but I was also going to be able to concentrate on helping customers fight the biggest weakness in their cybersecurity defense as my primary job. I was pretty elated and remain so to this day.

In the over five years since, as KnowBe4’s Data-Driven Defense Evangelist, I have taught hundreds of in-person presentations and online webinars. You can see many of my webinars here: www.knowbe4.com/webinar-library. You can download and read many of my whitepapers here: www.knowbe4.com/security-awareness-whitepapers. And you can request that I do a presentation to your company here: www.knowbe4.com/security-awareness-training-advocates. You can see dozens of my presentations for free on YouTube. I speak about a lot of topics beyond social engineering, including multifactor authentication, quantum, ransomware, passwords, password managers, nation-state hacking, and cryptocurrencies, but most of my presentations include something about fighting social engineering and phishing even if that isn’t the primary topic. I never miss a chance to educate listeners about the importance of focusing on preventing social engineering and phishing.

There is nothing else most organizations could do better to reduce their existing cybersecurity risk than to reduce social engineering and phishing threats. This book is the best advice for today’s world to help you fight social engineering and
