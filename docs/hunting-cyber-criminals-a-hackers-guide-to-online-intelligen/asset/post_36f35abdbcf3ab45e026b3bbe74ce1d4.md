
If I had manually searched for "cr0ok" in the w0m dataset, I would have missed this crucial clue (which is I'm sure so many others missed it as well).
Figure 18.16 shows the "announcement" table of w0m.ws database.

```
Dumping data for table announcement

INSERT INTO 'announcement' ('announcement', 'title', 'userid', 'startdate', 'enddate', 'pagetext', 'forumid',
views', 'announcementclicks') VALUES
(1), 'Trusted Section', 'We are under new management, as you can see there will be a launched section named
Trust which only will be available to the most elite members and/or contributors.
Payment & info: ke7hb@w0m.ws - 1, 369);
```

Figure 18.16

The announcement (which would not have been picked up as a forum post or message) says that "w0m is under new management ... payment and info: ke7hb@w0m.ws.
Looking further through the data, we can see that ke7hb was already a moderator on the w0m forum.
Investigation into that username indicates ke7hb was another one of w0m's usernames. So would appear that he is trying to shift ownership of the forum to himself (just under a different alias).
However, the database changelog (Figure 18.17) tells us a very different story.

```
Dumping data for table userchangelog

INSERT INTO 'userchangelog' ('changed', 'userid', 'fieldname', 'newvalue',
oldvalue, admin, 'username', 'ke7hb', 'cr0ok', 100, 1463697364),
62, 387, 'email', 'ke7hb@iranmail.com', 'cr0ok@swissjabber.ch', 100, 1463697364);
```

Figure 18.17

Looking at the "userchangelog" table, we can see that the ke7hb account was renamed to cr0ok, and the email address was changed from ke7hb@iranmail.com to cr0ok@swissjabber.ch.

Boom!
Refer back to Figure 18.15: Peace claims ownership for w0m hack. Peace loves getting attention from the media. He always has, and if he had not gone to the media claiming ownership for the hack, this would have been another dead end. Instead, now can conclusively link cr0ok with user Peace.

# Chapter 18 | Passwords, Dumps, and Data Viper 429

# Vanity over OPSEC, Earlier in Time

As I described earlier in this book discussing Cyber, Vanity always trumps OPSEC (operational security). Never underestimate the willingness of a threat actor to be careless in the name of fame or notoriety.

To this all off, Figure 18.18 shows a post by Cr00k on KickAss discussing w0m’s new management.

![](img/ceaab52f5a948b18995b8efe89758781_441_0.png)

Figure 18.18

He was bragging, plain and simple.

# Why This Connection Is Significant

Linking Cr00k to Peace is significant because Peace can also be linked to “Ping”, the former owner and admin of Hell Forum. There is quite a bit of published information about the identity of Ping (most of which is incorrect) and Hell Forum. The important point is that I have associated a member of TDO with Ping, the owner of the now-defunct Hell Forum means there is a good chance that he was still rolling with some of his old buddies.

This shifted the entire focus of my investigation from researching current TDO-related events to digging up as much information as I could about Hell Forum and its members.

As it turns out, I was right. Ping and his buddy Revolt turned out to not only be thick as thieves online, but they also knew each other in real life (they are only 1 year apart in age, and live about 5 miles from each other).

NOTE Regarding my comment on the majority of published information on Ping being "Incorrect." In an absolutely brilliant move, several members of Hell Forum tried pinning the identity of Ping onto someone else by creating fake internal drama within the group and ultimately "doxing" the wrong person (Dimitri Babu). This set off a chain reaction that led to the arrest of this person and severe threat intel reports being released, we confirmed the identity of Ping to be this fake person.

To his credit, there was one article on Motherboard by Joseph Cox he was able to uncover the truth behind the story. Dimitri gave the real identity of Ping. Unfortunately, he was only 15 at the time, so those records were sealed and his name was never released.

These kids put on a dog-and-pony show that was, frankly, an amazing display of how powerful a single blog post can be in manipulating the perception of investigators and the news media.

To doy, DTO's tactics were not changed. They regularly speak with reporters. In fact, a large majority of their stories come directly from "Dissent," who runs a blog at www.databreaches.net. In a direct conversation with her, Dissent told me that she has logged over 1000 hours chatting with DTO directly. She regularly relays the information they provide through her stories.

The point I am trying to make is that you should not always believe what you read, especially if the source of the information is coming directly from the targets you are investigating!

# Starting Small: Data Viper 1.0

When I started this quest, I was accessing all sorts of information on forums and saving everything manually (literally using "Save As" to save each important page I across). Result was a mess of HTML files that I needed to be able to reference. That, combined with all of the data sets I was collecting, turning into a nightmare for manual "grep" searching.

I started investigating different solutions, and before building a full Elasticsearch database, I stumbled across DEVONthink, an amazing search tool for Mac. DEVON is available at www.devontechnologies.com.

DEVON is a data collection and indexing tool. Drag data into it, organize by folders, and My DEVON database have a pretty sweet tool.

My DEVON database contains all of the old data that I was able to scrape together. Figure 18.19 shows a search run for "cr00k" just within the KA (KickAss) folder.

# Chapter 18 — Passwords, Data, and Data Viper 431

| Index | | | |
|---|---|---|---|
| Dday | | | 43910 | USA full (SSN, DOB, ADDRESS.html) |
| Dday April | 78 | USA full (SSN, DOB, ADDRESS.html) |
| Blackstuff | | | PayPal page (source: .db) |
| Exploit | 174217 | | PayPal page (source: .db) |
| Galaxy2 | 1358 | | Biggest & best service around |
| Hell Pages | 9058 | | Biggest & best service around |
| Hell2 Messages | 176/385 | | [TUT] How to use 201 in counts.html |
| Messages | 186/569 | | [TUT] How to use 201 in counts.html |
| KA | 75 | | N.A. |
| Final Post_files | | | N.A. |
| TGO | 13 | | Alpha 2.0 Spreading through well-known website(s).html |
| XMPP Counts | 62 | | Alpha 2.0 Spreading through well-known website(s).html |
| Time | | | php-web-works.html |
| All Images | 1676 | | |
| All PDF Documents | 395 | | |
| Duplicates | 179008 | | |

![](img/ceaab52f5a948b18995b8efe89758781_443_0.png)

# Summary

This chapter discussed how hacked databases and password lists can be used to find new information on your targets. A real example of user F3ttywap was used to help finish the threat actor matrix that we have been building from the previous chapters. Since password reuse is common among many people (even threat actors), you should always try to create new associations by looking for other accounts using similar passwords.

This chapter also took a deep dive into Data Viper (www.dataviper.io) and how information from clearweb and dark forwebs can be used to trace the movements of threat actors and in the right context can ultimately lead to their identification. Since Data Viper is a homegrown application, this chapter also discussed ways in which you can build your own using freely available tools and data sets.
