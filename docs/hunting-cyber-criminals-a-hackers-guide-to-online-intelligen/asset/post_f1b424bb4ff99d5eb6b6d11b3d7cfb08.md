
The point of this rant is: be careful how much information you share and with who. There can be significant consequences in publishing someone's personal information. The result of this particular article, as we will see, set off a chain of events intended to cause me "pain."

The article sparked a lot of interest on the KickAss forum and personally made me a target for attacks. When all of this went down, Cyper (aka NSA), the forum's admin, decided to put a bounty on my site with the forum post "Own this rat site" (Figure 17.6).

![](img/ceaab52f5a948b18995b8efe89758781_397_0.png)

Figure 17.6

To my point regarding the publishing of the article, I can't say I appreciate the fact that I was personally exposed. There are consequences to exposing someone's personal information, as evidenced by the following post by user "deafrow" (Figure 17.7).

Luckily, I am one of those people who believe there is an opportunity in every problem—and in this, I was right.

Unbek to all, I had a second alias on the forum, "Argon." At this time, Argon was undergoing an application process to be accepted into Cyper's personal hacking group. The contest against my site proved to be an amazing opportunity. What better way to flex my skills as a blackhat ninja hacker to hack my own site?

I did it.

## Chapter 17 ■ Profile Tracking and Password Reset Clues 385

![](img/ceaab52f5a948b18995b8efe89758781_398_0.png)

### Figure 17.7

I set up a performing PHPMyAdmin panel in a remote directory on one of my sites. Anyone performing server recon who would be able to bruteforcing using Wfuzz (as described in Chapter 7) would have been able to find it.

My cover story was simple. Once I found the panel, I ran a search for my email/password combinations that could be discovered from my email addresses (this technique will be discussed in the next chapter).

I set the PHPMyAdmin login to another username/password combo from a random data leak. Using the passwords “discovered” from various data leaks, I pretended to gain access by bruteforcing the PHPMyAdmin panel.

To prove I was there, “hacked” my own WordPress site by directly modifying the WP database table, and replaced the front page with the image shown in Figure 17.8.

![](img/ceaab52f5a948b18995b8efe89758781_398_1.png)

### Figure 17.8

### 386 Part IV | People Hunting

But why stop there? I assumed Cyper and his team would want to personally verify the access and login themselves. Prior to my victory announcement, I took the liberty of setting up strict firewall rules on my server to completely block any connections from known TOR, VPN IP, proxy, or other bad IPs. I then set up logging to monitor for any incoming connections.

When the trap was set, I made a celebratory post on the forum's contest thread (Figure 17.9).

![](img/ceaab52f5a948b18995b8efe89758781_399_0.png)

Figure 17.9

Not bad, right? How many people would expect someone to hack their own website?

NSA asked me a list of questions about how I was able to do it, all of which were completely plausible; and it worked!

NSA and his team had their fun in playing around my panel, and as my reward, I got to record all of their IP information. The PHPMyAdmin URL was so obscure (and so brand new) that they were obviously relevant—which included the fake web scraping bots that suddenly appeared.

The point of this story is that if we are going to SE, why hold back? Sometimes the most outrageous ideas are the best ones.

```
EXPERT TIP: JOHN STRAND

When you start talking about op-sec for adversaries, it isn't just a matter of op-sec from the perspective of getting them to open any old document and using that to hope get some information about them. It's a matter of using the right bait.
I've learned over the years of doing this (quite a while) that fake documents look fake. If you can put tracking elements inside a real document, that's a lot better.
```

## Chapter 17 Profile Tracking and Password Reset Clues 387

Macros will freak an adversary out. If you try to drop a macro in a document, they're not going to open it. If you try to put a macro in an Excel spreadsheet, macros are always in Excel spreadsheets...so they are going to open it, and they're not? It's defer.

On the other hand, if you tried to put a link in a cascading stylesheet (CSS), or an image source tag in the metadata of a document, your likelihood of them actually opening and having it beacon back is now a lot better.

Some of my favorite ideas to get adversaries to run things like simple ideas. Just set up a directory on a website that serves VPN, and have an executable that does the automatic VPN configuration and then you create that executable with its own functionality. Or you can even sign that executable, wait for any lookups on that code signing certificate.

### Everyone Gets'd—a Lesson Learned

The point of this story is that if we are going to SE, why hold back? Sometimes the most outrageous ideas are the best ones.

The moral of the story—don't store cookies in TOR, and don't be so quick to click on links! (Duh, right?)

## The End of TDO and the KickAss Forum

In my official report on TDO, I propose a theory Figure 17.10 shows a copy of the TDO's message (which has since closed).

![](img/ceaab52f5a948b18995b8efe89758781_400_0.png)

Figure 17.10

### 401

Somewhere in heated conversation, Cyper dropped a message for the KickAss (which I immediately recognized). I clicked the link to see what was (the same one I accidentally clicked on in this chapter).
