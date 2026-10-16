
$ sherlock --fo smithsearch jsmith smith johnsmith
[*] Checking username jsmith on:
[+] 7Cups: https://www.7cups.com/@jsmith
[+] 9GAG: https://www.9gag.com/u/jsmith
[+] About.me: https://about.me/jsmith
[+] Academia.edu: https://independent.academia.edu/jsmith
[+] Airbit: https://airbit.com/jsmith
[+] Airliners: https://www.airliners.net/user/jsmith/profile/photos
[+] AllMyLinks: https://allmylinks.com/jsmith
[+] Apple Developer: https://developer.apple.com/forums/profile/jsmith
[+] Apple Discussions: https://discussions.apple.com/profile/jsmith
[+] Archive of Our Own: https://archiveofourown.org/users/jsmith
[+] Archive.org: https://archive.org/details/@jsmith
[+] Arduino: https://create.arduino.cc/projecthub/jsmith
[+] Asciinema: https://asciinema.org/~jsmith
[+] AskFM: https://ask.fm/jsmith
[+] Audiojungle: https://audiojungle.net/user/jsmith
[+] BLIP.fm: https://blip.fm/jsmith
[+] Behance: https://www.behance.net/jsmith
[+] BiggerPockets: https://www.biggerpockets.com/users/jsmith
[+] Bikemap: https://www.bikemap.net/en/u/jsmith/routes/created/

LinkedIn has been around for about two decades as of this writing. In spite of a number of competitors (such as Plaxo) going out of business or just no longer being in the space, LinkedIn is still around. It continues to expand its offerings beyond the very early days, when it was basically a contact manager. These days, LinkedIn is a business networking opportunity, highly useful for those in sales. It is also a great source for identifying jobs you may be interested in. It seems like human resources people, specifically recruiters, commonly use LinkedIn to find people to fill positions, whether it's an internal recruiter or someone who works for a recruiting company.

Because of the amount of business information LinkedIn collects, we can make use of it as a hunting platform. Especially with the paid memberships, LinkedIn does a lot of analytics about the businesses that make use of it, as well as the people who are on the site. If you are looking for information about a target, LinkedIn provides a lot of detail. Just as one example, [Figure 4.8](#c04.xhtml#c04-fig-0009) shows some statistics about applicants for a position that is open and advertised through the Jobs section of the website. This information requires a Premium subscription. We can see that the position attracts educated applicants. You can start to get a sense of the workforce by looking at these statistics across multiple positions.

![FIGURE 4.8 LinkedIn job statistics](images/c04f008.png)

[**FIGURE 4.8**](#c04.xhtml#R_c04-fig-0009) LinkedIn job statistics

Job listings are another place to look for details beyond the statistics about applicants and the workforce overall. What we can see from these listings is technology that may be in place within the organization. A listing for a network security engineer has requirements as shown in [Figure 4.9](#c04.xhtml#c04-fig-0010). While some of these requirements are generic, there are also some that are very specific about the technology in use in the network. For example, it appears that the company may be using Check Point on their site and Palo Alto Networks firewalls. Additionally, it has Cisco routers and switches in its network. This is a foothold. We can now start thinking about how to attack that sort of infrastructure. Cisco devices, for sure, have tools that can be run against them for various auditing and attack purposes.

![FIGURE 4.9 Job requirements for a network security engineer](images/c04f009.png)

[**FIGURE 4.9**](#c04.xhtml#R_c04-fig-0010) Job requirements for a network security engineer

We don't have to limit ourselves to the web interface, though, since it can be tedious to keep typing things and flicking through pages. Sometimes you want to be able to script a search without writing a program or manually using a web page. Formerly, there was a tool called InSpy that worked well for searching through LinkedIn. Unfortunately, the latest version of InSpy available on Kali, 3.0.0, generates 404 errors trying to search for details. The instructions also require the use of an API key. With a little work, though, you can use another tool to do the LinkedIn searching for you.

Beyond jobs, though, we can use LinkedIn to harvest information about people. There are a couple of reasons to look up people. One is just to get some names and titles that you may use later. Another is that even if job descriptions don't have information about technology, when people post their job responsibilities, they very often do. You can also get details about their certifications. Someone with a load of Cisco certifications, for example, is probably employed at a company that has a lot of Cisco equipment. Don't overlook nontechnical roles either. Anyone may provide a little insight into what you may find in the organization. You may get information about telephone systems and document management systems that the company uses, even if the employee isn't an administrator.

We will take a look at a tool called crosslinked.py here to do some searching for us.

**CrossLinked Results from an Employee Search**

```
 $ git clone https://github.com/m8r0wn/crosslinked
  
 Cloning into 'crosslinked'…
 remote: Enumerating objects: 166, done.
 remote: Counting objects: 100% (27/27), done.
 remote: Compressing objects: 100% (25/25), done.
 remote: Total 166 (delta 15), reused 4 (delta 2), pack-reused 139
 Receiving objects: 100% (166/166), 66.85 KiB | 2.48 MiB/s, done.
 Resolving deltas: 100% (72/72), done.
 $ pip3 install -r requirements.txt
 $ python3 crosslinked.py Wiley -f wiley.com\flast --search google
  
      _____                    _             _            _ 
     /  __ \                  | |   (x)     | |          | |
     | /  \/_ __ ___  ___ ___ | |    _ _ __ | | _____  __| |
     | |   | '__/ _ \/ __/ __|| |   | | '_ \| |/ / _ \/ _` |
     | \__/\ | | (_) \__ \__ \| |___| | | | |   <  __/ (_| | @m8sec
      \____/_|  \___/|___/___/\_____/_|_| |_|_|\_\___|\__,_| v0.2.1
  
     
 [*] Searching google for valid employee names at "Wiley"
 [*] 99 https://www.google.com/search?q=site:linkedin.com+in+"Wiley"&num=100&start=0 (200)
 [*] 198 https://www.google.com/search?q=site:linkedin.com/in+"Wiley"&num=100&start=99 (200)
 [*] 297 https://www.google.com/search?q=site:linkedin.com/in+"Wiley"&num=100&start=198 (200)
 [*] 298 https://www.google.com/search?q=site:linkedin.com/in+"Wiley"&num=100&start=297 (200)
 [*] 298 https://www.google.com/search?q=site:linkedin.com/in+"Wiley"&num=100&start=298 (200)
 [*] 298 https://www.google.com/search?q=site:linkedin.com/in+"Wiley"&num=100&start=298 (200)
 [*] 298 https://www.google.com/search?q=site:linkedin.com/in+"Wiley"&num=100&start=298 (200)
 [*] 298 names collected
  
  
 
```

The results of the search are placed in a comma‑separated values file named names.csv. This is not a perfect utility, however, since it is not searching for employees at Wiley. Instead, you are getting everything that may have Wiley as part of the results, including people named Wiley. This includes people like a consultant named Calvin Wiley.

#### Twitter

Another common social networking site or service is Twitter. There is a lot posted to Twitter that can be of some use. Again, programmatic access to Twitter is useful. You can search using the regular interface, but it's sometimes helpful to be able to use other tools. To gain access to Twitter programmatically, you need to get an API key. This means you need to tell Twitter you are creating an application. You can easily tell Twitter you are creating an application without any special credentials through the Twitter developer's website. When you go through the process to create an application, what you are doing is creating identification information that your app needs to interact with the Twitter service. In [Figure 4.10](#c04.xhtml#c04-fig-0011), you can see keys and access tokens for an app.

