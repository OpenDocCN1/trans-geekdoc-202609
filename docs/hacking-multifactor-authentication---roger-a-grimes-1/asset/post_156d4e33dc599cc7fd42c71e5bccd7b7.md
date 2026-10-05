
# Introduction

This book came about through an interesting happenstance. Arguably, the world's most infamous hacker, Kevin Mitnick, co-owner and Chief Hacking Officer at KnowBe4, Inc., did a presentation that included showing how he could easily “hack around” two-factor authentication using a simple phishing email. Kevin is a lot more famous than I am, and his demonstration was viewed by thousands of people. And that many people wrote to him to get more details.

Many people wrote and interviewed the KnowBe4 (who I also work for) public relations team asked if I could answer queries Kevin couldn't get. I was glad to. I've got decades of experience in hacking covered security topics frequently if people asked about the exploit Kevin used in the MITRE list of Vulnerabilities and Exposures (cve.mitre.org). The CVE is where most cybersecurity vulnerabilities, new or old, are listed and tracked. When a report is made to the CVE, it includes relevant details. Most of us in the cybersecurity world check it to see what exploits have been found and to see if we really need to be worried about them.

I laughed. The technique Kevin demonstrated (which is called session cookie hijacking and is covered in Chapter 6, “Access Control Token Tricks” of this book) has been around for decades. It's not new at all. In fact, it is one of the most common forms of network hacking. Dozens of free hacking tools are available that hackers use; it's likely used to take over millions of user accounts over three decades. It's been used to take over accounts protected by two-factor authentication, at least since the late 1990s. It's the opposite of new.

I was surprised when I talked to the beat reporters and computer security people I knew, most thought it was a new attack. So, not everyone and regular people did not know that it wasn't, but knowledgeable, experienced computer security people—who expected to know—didn't know that. It was surprising to me.

I was also surprised that many of the people I thought the attack was due to a vulnerability in LinkedIn, the website Kevin used in his demonstration. It wasn't. What Kevin showed could be used against hundreds of popular sites, and LinkedIn, in particular, didn't have a flaw that they were going to have to fix. It was an attack against a very common form of multifactor authentication and how it worked in general. No patch was coming to fix some flaw. And you could update the multifactor authentication solution that was used to prevent the particular type of attack Kevin demonstrated, but it could be attacked at least in another different ways, as with any multifactor authentication method.

To many of the people I talked with, I shared that I knew of at least 10 ways (as I quickly counted) to hack different forms of multifactor authentication. They were all shocked. As a result, I decided

to write a column about it for CSOonline (www.csoonline.com), where I was a writer at the time. By the time I finished the column (www.csoonline.com/article/3272425/authentication/11-ways-to-hack-2fa.html) in May 2018 I came up with 11 ways.

I was sharing the news of my column with the CEO of KnowBe4, Stu Sjouwerman, the next morning when he wisely suggested I create a presentation on the topic and start giving it. Within a few days, I created a new presentation 12 Ways to Defeat Multi-Factor Authentication (info.knowbe4/webinar-12-ways-to-defeat-mfa). As I did more research and thinking, I quickly came up with ways to hack MFA nearly every day.

I'm over 50 ways, all of which I share in this book. The presentation turned into a whitepaper. At KnowBe4, the average whitepaper is three to five pages long; mine was 20 pages. It was the longest whitepaper in the history of KnowBe4, and it quickly became a running joke around the office. I shared that I had originally created a rough draft double the size and that the 20 pages were my trimmed-down version after their chiding. That then led it into becoming a short e-book (www.knowbe4.com/how-to-hack-multi-factor-authentication) at 40 pages.

I began my presentation around the world, including at the biggest computer security conferences, RSA and Black Hat. In both places I had standing room-only crowds and lines of attendees trying to come in some of the hack discussions. My 12 Ways to Multi-Factor Authentication presentation was so long that I have to choose which of the hacks I am going to share with audiences, although Kevin's original MFA hacking demo is still clearly a crowd favorite (and I asked the URL for it in this book).

Jim Minatel, my longtime friend and acquisitions editor at Wiley, came to see my presentation at RSA and saw the enthusiastic crowds. I was sick as a dog when I gave the presentation; in fact, I was hospitalized for the week after the presentation with an acute, life-threatening illness. I felt like I had a terrible job to present managing. I would certainly love a favor do-over. But Jim saw the crowds and the energy the material generated and asked if I would write a book on the subject. I said yes over lunch, and this is true. The best part is that I've given hundreds and hundreds of pages to share everything I know on the subject. Even then I'm sure more books of the same size could be written on the subject. Multifactor authentication and its weaknesses are many. In truth, even this book is just scratching the surface. It's 500-plus pages of summary material. I hope all readers understand the strengths and weaknesses of multifactor authentication and that MFA developers will create better, more secure solutions.

The ultimate objective of this book is to properly frame the security and weaknesses of all MFA solutions. If you only know the benefits and none of the risks, you're more likely to implement an MFA solution without the appropriate policies, controls, and education. This book is a push-back against the overwhelming marketing messages by some MFA vendors. MFA solutions can significantly reduce many faults of cybersecurity, but they aren't perfect panacea and does not mean we can throw away all the previous security lessons learned. If you come away with a suitable understanding of what MFA can and can't, and change your practices and controls appropriately, I've done my job.

# Who This Book Is For

This book is primarily aimed at anyone who is in charge of or managing their organization's computer security and, in particular, logon authentication. It is for anyone who is considering, buying, or using multifactor authentication for the first or the tenth time. It is for developers and vendors who make multifactor authentication solutions. Prior to this book there has not been a single place where anyone, customer or vendor, could go learn about all the common ways multifactor authentication can be hacked. Now there is that source, although I'm sure I haven't covered every hacking method, defense, and caveat. But I tried.

It is mostly for the people who have heard the great promises that multifactor authentication will give and somehow equate those with a larger falsehood, that using MFA "I can't get hacked! Nothing could be further from the truth." This book is your counter when anyone tries to convince you that by using MFA you don't have to worry about hacking anyone. That isn't and will never be true.

It also dispels the naive notion that we really want 100 percent security. We don't. Society wants a solution that impacts the least and provides "Just OK protection." It is a hard reality that both administrators and developers learn in the marketplace of computer security products. Some of the best, really secure computer products never get purchased by more than a few companies, and end up on the heap of unused products.

In this book, I remind us of the famous quote given by Jack Nicholson's character, Colonel Nathan Jessup, in the 1992 movie A Few Good Men: "You can't handle the truth! You may not like to hear that we don't want the best security, but ignore what the user wants at your peril. So, the purpose of this book is not only about developers and customers learning all the ways to hack MFA, but also about when layered security is just too much security.

# What Is Covered in This Book?

Hacking Multifactor Authentication contains 25 chapters separated into three parts:

Part 1: Introduction Part I discusses authentication basics and the problems that MFA is trying to solve. It includes the background facts you'll need to know to understand why MFA is a favored authentication solution and how it is hacked.

Chapter 1: Logon Problems Chapter 1 covers the central problems that MFA is trying to solve. MFA did not come out of the book. Password and single-factor solutions failed so often that better and improved authentication solutions were invented. Learn about the problems MFA is trying to solve.

Chapter 2: Authentication Basics Authentication isn't one process—it's a series of connected processes with a multitude of different components. Any of the steps and components can be hacked. To understand how MFA can be hacked, you first have to
