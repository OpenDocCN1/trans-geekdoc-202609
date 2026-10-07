
# 92 Part I | Network Exploration

![](img/ceaab52f5a948b18995b8efe89758781_114_0.png)

Figure 5.10

| 185.166.213.155 | 185.166.213.155,duacrypt.com | 2018-12-17 07:35:05 | FINISHED | 439 | 2 4 5 |

Figure 5.11

Digging into our results, it is immediately obvious that the UI and graphical elements within HX are significantly improved from those found in the standard version of SpiderFoot, as shown in Figure 5.12.

> When working with executive clients, having graphical elements can often make the difference between a good report and an excellent report. I have found that most executives don't want a report loaded with a bunch of words that most likely won't ever have the time to read. They want concise results, bullet points, and graphical elements they can use to easily present the findings to their board or executive team.

Overall, the results between the free and premium version of SpiderFoot are very similar. The majority of returned results (Figure 5.13) come back to the IP's subnet being on about 30 different blacklists. In addition, the HX version found an additional username associated with our target, a Reddit account called "dualcrypt" (https://www.reddit.com/user/dualcrypt). A great lead, but unfortunately the user has not posted anything.

Admittedly, this was a very difficult target with very little discoverable information. Let's see how the results for SpiderFoot HX compare to its open-source counterpart when scanning uberpeople.net, a much more popular target (Figure 5.14).

![](img/ceaab52f5a948b18995b8efe89758781_115_0.png)

Figure 5.12

# 94 Part I | Network Exploration

| Correlation | Data Elements | Criticality | Created |
|---|---|---|---|
| Entity blacklisted by multiple sources: 185.165.169.0/24 | 19 | MEDIUM | 2018-12-17 09:02:13 |
| Entity considered malicious by multiple sources: 185.165.169.0/24 | 27 | HIGH | 2018-12-17 09:02:12 |
| Hostname only from proprietary source: hostmaster.duacrypt.com | 1 | LOW | 2018-12-17 09:02:13 |
| Hostname only from proprietary source: duycrypt.com | 1 | LOW | 2018-12-17 09:02:13 |
| IP address only from proprietary source: 149.129.212.248 | 1 | LOW | 2018-12-17 09:02:13 |

**Figure 5.13**

![](img/ceaab52f5a948b18995b8efe89758781_116_0.png)

**Figure 5.14**

The HX scans against **uberpeople.net** show 629 results with 1 critical and medium-risk items (Figure 5.15).

![](img/ceaab52f5a948b18995b8efe89758781_116_1.png)

**Figure 5.15**

Our earlier scans of **uberpeople.net** using the open-source version of SpiderFoot yielded 605 total results, while the improved HX version yielded 629 results. The 24 additional matches may not appear significant at first glance, though numbers could easily be a result of many factors, including our sample test sites. Depending on your job function, the added visual components and ability to export usable graphical elements can make this a very worthwhile subscription upgrade.

# Chapter 5 ■ Automated Tools for Network Discovery 95

# Intrigue.io

Intrigue was developed by security developer and researcher Jonathan Cran, and you can download it at www.intrigue.io. Intrigue is the open-source engine that powers Intrigue, a platform for attack surface discovery. According to Cran, Intrigue Core was designed around the concept of graph-based discovery, allowing it to automate the process of attack surface discovery and intelligence gathering.

The primary focus of Intrigue is to discover assets and “interesting things” about an organization from an external perspective. It is also becoming useful as a platform for dev-ops and security teams to pull security-related information together in a single pane of glass, allowing them to easily find connections between organizational entities.

Within Intrigue, every bit of information (or intelligence) is classified as an entity. Intrigue's flexible data model uses tasks to perform functions—either manually or automatically. Each entity can, be iterated upon with more tasks—Intrigue uses this data model, and another iteration called machines, to flesh out the assets and vulnerabilities of an organization.

What I find most impressive about Intrigue is its ability to process, detect, and automatically enrich newly discovered entities. For example, let's say you are running a wide search on a domain name. Intrigue may bring back a number of entities including an IP address, related domain names, and subdomains (just to name a few). By the “enrich” option, Intrigue will take each of these new entities and run an entire battery of tests. The combinations and results quickly become exponential, saving you a significant amount of time in your initial discovery.

Intrigue can perform a large number of tasks, including:
- Open searches: Censys, SecurityTrails, and Shodan
- WHOIS lookups
- Public Trello board
- Brute forcing of S3, and other public buckets
- Directory brute forcing
- DNS/name enumeration
- Certificate transparency searches (crt.sh)
- Related nameserver and DNS record checks
- Related WHOIS checks
- FTP service discovery and data collection
- SSH, RDP, and VNC (with screenshots)
- NSE scanning
- GitHub searching

> Intrigue Core is incredibly powerful at the application layer due to its library. It was designed specifically for application-layer fingerprinting and is kept based on the ever-increasing data we have access to through Intrigue.io. This gives the core version-specific fingerprinting and vulnerability mapping. With many built-in tasks, as well as notifications and the concept of issues, Intrigue Core is more of a platform than a tool. The task and entity concept makes it easy to extend the app's functionality. And as you continue finding new assets, vulnerabilities, and misconfigurations, the platform keeps evolving.

Use Intrigue to kick off a basic automated query against a URI, click the Start button.

# Entities Tab

This is where magic of Intrigue happens. The Entities tab displays a list of all entity types. For duacrypt.com, we only see six types. For more popular targets (which we will see later in this section), this number will be higher. The following are the entity types for the discovered results of duacrypt.com (Figure 5.17):
- Domains: 3
- Uri: 1
- IpAddress: 1
- Netblock: 1

# Chapter 5 ■ Automated Tools for Network Discovery 97

![](img/ceaab52f5a948b18995b8efe89758781_119_0.png)

Figure 5.16

| | details |
|---|---|
| IPAddress: 185.165.169.124 | Seychelles |
| Domain: njalla.no | A: 1 |
| Domain: njalla.io | A: 1 |
| Domain: duacrypt.com | A: 1 |
| NetBlock: 185.165.168.0/22 | SC-FLOKINET-LTD-20160826 |
| Url: http://www.duacrypt.com | Server: App: Title: |

Figure 5.17

Clicking any of those entities will give us more information and transformations that we can run. Figure 5.18 shows the entity detail page; on the right, we can see a list of options for new tasks we can run. Clicking the task type shows a plethora of follow-on scans that can run on the domain (Figure 5.19), including searching CRT.sh (which we discuss in Chapter 10), publishing Google Groups leaks, Trello leaks, enumerating nameservers, Whois search, and much more. Each entity type has its set of additional tasks that can be run to find additional information on your target.

# 98 Part I | Network Exploration

![](img/ceaab52f5a948b18995b8efe89758781_120_0.png)

Figure 5.18

![](img/ceaab52f5a948b18995b8efe89758781_120_1.png)

Figure 5.19

# Chapter 5 Automated Tools for Network Discovery 99

From the screen shown in Figure 5.20, we can also expand and see greater detail on the discovered entity. Clicking the IP address shows us general information about it, including its potential location. On the right, we can pull up our task list and run new actions based on this IP. Notice that the task types in Figure 5.20 are different from the previous task types. That's because the task types will change based on what can be performed with the given entity type.

![](img/ceaab52f5a948b18995b8efe89758781_121_0.png)

Figure 5.20

### ### Analyzing uberpeople.net

Now that we have an understanding of the capabilities of Intrigue, let's restart the process to look at **uberpeople.net**. Figure 5.21 shows the Add Entity screen configured to kick off a scan for **uberpeople.net**.

Looking at the Results tab, we can see that a number of tasks have been automatically run on **uberpeople.net**.

Figure 5.22 shows a small sample of the different tasks that were automatically run, and the number of discovered entities per task.
