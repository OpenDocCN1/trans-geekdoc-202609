# Chapter 5 ■ Automated Tools for Network Discovery 95

# Intrigue.io

Intrigue was developed by security developer and researcher Jonathan Cran, and you can download it at www.intrigue.io. Intrigue is the open-source engine that powers Intrigue, a platform for attack surface discovery. According to Cran, Intrigue Core was designed around the concept of graph-based discovery, allowing it to automate the process of attack surface discovery and intelligence gathering.

The primary focus of Intrigue is to discover assets and “interesting things” about an organization from an external perspective. It is also becoming useful as a platform for dev-ops and security teams to pull security-related information together in a single pane of glass, allowing them to easily find connections between organizational entities.

Within Intrigue, every bit of information (or intelligence) is classified as an entity. Intrigue's flexible data model uses tasks to perform functions—either manually or automatically. Each entity can, be iterated upon with more tasks—Intrigue uses this data model, and another iteration called machines, to flesh out the assets and vulnerabilities of an organization.

What I find most impressive about Intrigue is its ability to process, detect, and automatically repress newly discovered entities.

For example, let's say you are running a wide search on a domain name. Intrigue may bring back a number of entities including an IP address, related domain names, and subdomains (just to name a few). By using the “enrich” option, Intrigue will take each of these new entities and run an entire battery of tests on each. The combinations and results quickly become exponential, saving you a significant amount of time in your initial discovery efforts.

Intrigue can perform a large number of tasks, including:

+   Open database searches: Censys, SecurityTrails, and Shodan

+   WHOIS lookups

+   Public Trello board checks

+   Bruteforcing of S3, Trello, and other public buckets

+   URI spiring

+   Directory and filename bruteforcing

+   DNS/name server enumeration