# 20.6.3 Lockdown and Quarantine.

More drastic anti-Trojan measures include preventing unauthorized changes or additions to executables and preventing systems from connecting to networks until they have been vetted. The idea of defeating malicious executables by freezing the operating system, and authorized applications in a known good state, goes back a long way, at least to the early days of antivirus efforts. However, the complexity of most operating systems and application code today makes such an approach challenging at best. Consider the emergence of Patch Tuesday as a standard means of maintaining the world's most widely used operating system. Indeed, for many years now, a lot of software development has been predicated on the assumption that patches and updates can always be pushed out if needed, arguably leading to far less rigor in coding practices than when production code was burned to disk, at considerable expense, and changes required further shipments of disks.

The idea of quarantining computers when they attempt to connect to a network, using some form of network access control, offers a slightly different approach to the idea of locking down machines so that unauthorized code cannot be installed. Some enterprise network security managers have pursued this approach because it is increasingly difficult to control some network end points, such as the company laptop that travels with the employee to client sites and conferences, hotels, and WiFi hot spots, even spending time in the employee's car and home. Laptops used in this manner face any number of attack vectors. Traditional defense mechanisms can be applied to these end points, including password protection, biometric authentication, disk encryption, and antivirus programs. However, these may not be enough, as many enterprises have discovered to their cost. So why not prevent these machines from connecting to the enterprise network until they have been scanned for unauthorized executables, like a routine health check? This approach holds promise but is not easy to implement. Furthermore, it leaves machines open to attack while they are away from the corporate network. A spam-distributed phishing exercise or screensaver Trojan could still lobotomize an end point between checkups and compromise confidential personal or corporate data. As you can see from Exhibit 20.5, a table compiled by Symantec in 2011 to show prices paid for various forms of data in the underground economy in 2009 and 2010, the financial incentives for such activities are real.

# EXHIBIT 20.5 Table of Prices Paid for Data Traded in the Underground Economy⁴⁷

| Overall Rank |  | Percentage |  | 2010 Price Ranges |
| 2010 | 2009 | Item | 2010 | 2009 | |
|---|---|---|---|---|---|
| 1 | 1 | Credit card information | 22% | 19% | $0.07-$100 |
| 2 | 2 | Bank account credentials | 16% | 19% | $10-$900 |
| 3 | 3 | Email accounts | 10% | 7% | $1-$18 |
| 4 | 13 | Attack tools | 7% | 2% | $5-$650 |
| 5 | 4 | Email addresses | 5% | 7% | $1/MB-$20/MB |
| 6 | 7 | Credit card dumps | 5% | 5% | $0.50-$120 |
| 7 | 6 | Full identities | 5% | 5% | $0.50-$20 |
| 8 | 14 | Scam hosting | 4% | 2% | $10-$150 |
| 9 | 5 | Shell scripts | 4% | 6% | $2-$7 |
| 10 | 9 | Cash-out services | 3% | 4% | $200-$500 or 50%-70% of total value |