
## Threat Hunting Example

Let’s walk through a short example of threat hunting using mining, clustering, grouping, and stack counting. For this example, I am tasked with investigating a potential malicious domain called `success20.hopto.org` (warning: this website is malicious, so don’t try this unless you have the right tools for testing!). I’m using Cisco Threat Response to perform threat analysis of the suspicious domain in this example, but similar tools are available, such as Sqrrl. [Figure 8-21](#ch08.xhtml#ch08fig21) shows using Cisco Threat Response to research `success20.hopto.org`.

![FIGURE 8-21 Cisco Threat Response Analyzing success20.hopto.org](Images/08fig21.jpg)

**FIGURE 8-21** Cisco Threat Response Analyzing success20.hopto.org

Mining is represented by all of the datapoints that are pulled from investigating the suspicious domain. I can see different malicious files, domains, and SHAs that all have some relation to `success20.hopto.org`, represented as “Grouping” because each group is based on a shared datapoint. [Figure 8-22](#ch08.xhtml#ch08fig22) shows the grouping of other domains that are associated with `success20.hopto.org` via the same domain owner. This is useful for learning about all domains associated with a potentially malicious domain to block everything owned by the domain owner. It is very common for the domain owners of malicious domains to own multiple malicious domains. This allows them to cycle through domains as the domains are flagged as malicious and blocked by security tools.

![FIGURE 8-22 Other Domains with Association to success20.hopto.org](Images/08fig22.jpg)

**FIGURE 8-22** Other Domains with Association to success20.hopto.org

If I want to use stack counting, I can search for a specific thing, such as count how many domains are associated with the domain owner of `success20.hopto.org`. If I’m looking for other suspicious domains associated with the domain owner, I would create a stack, which would find eight other URLs as shown in [Figure 8-22](#ch08.xhtml#ch08fig22). Stacking is more useful when searching across a large dataset with expectations of having multiple hits.

Clustering would be represented by searching across a lager dataset for similar datapoints to see if a new relation could be established as well as to reduce what the threat hunter needs to look for. [Figure 8-23](#ch08.xhtml#ch08fig23) shows searching for interaction with `success20.hopto.org` within different security tools and threat intelligence data available within my SOC to see how many sightings have been identified. Based on the number of sightings and judgments (risk scoring) that show `success20.hopto.org` is malicious, I can quickly determine the website and its associated artifacts are all malicious, allowing for a quick validation and summary of what the SOC needs to block.

![FIGURE 8-23 Searching success20.hopto.org Across Multiple Resources](Images/08fig23.jpg)

**FIGURE 8-23** Searching success20.hopto.org Across Multiple Resources

This is just a simple example of how different datapoints about a suspicious domain can help a threat hunter lead to a conclusion about what is being researched. These techniques also help identify other associated risk, allowing for a complete analysis of all potential risk with an artifact, domain, or other topic that needs to be analyzed. Security tools can make research easy, and for very large datasets such as big data, data aggregation and correlation are required. [Chapter 6](#ch06.xhtml#ch06) covered how to work with big data.

> **Note**
>
> Websites such as Malware Domain List ([http://www.malwaredomainlist.com/mdl.php](http://www.malwaredomainlist.com/mdl.php)) and Internet Storm Center ([https://isc.sans.edu/suspicious_domains.html](https://isc.sans.edu/suspicious_domains.html)) are resources that provide indicators of compromise (IOCs) you can use for research purposes. Be cautious when using these and similar resources as they contain real malicious domains!

### Eradicate

Once your incident response team has contained the threat through threat hunting and segmentation/isolation of impacted systems, it is time to perform steps to eradicate all aspects of the threat. All aspects of a threat include all impacted systems and all vulnerabilities that were used to initiate the compromise and spread the threat. For example, a specific exploit could be used to gain access to one system, but another exploit could be used on that same system to get a domain login, allowing for malware to spread to other systems. In this example, eradication would include removing the malware, changing the domain passwords, and providing a response to the vulnerabilities that permitted the initial access to the first victim (commonly called “patient zero”) as well as the vulnerability that led to the larger compromise. The eradication step assumes you have contained the threat.

#### System Order

When performing eradication steps, you want to start with the directly impacted systems. These are the systems that are confirmed as compromised and must be addressed to reduce the risk of further spreading of the threat. Next, all systems that are or could be in contact with any impacted system must be evaluated to ensure they have not been compromised. By confirming all systems within reach of all infected systems are not compromised, your incident response team is validating the *possible* scope of the breach.

I specifically point out you are possibly scoping the breach based on how malware can jump between systems and not infect every system contacted during a major outbreak. Many forms of malware will look for specific indicators before launching an attack, the goal being to avoid deception technology such as honeypots and limit exposure to only systems that are a high percentage of successful compromise, meaning only attacking systems that are likely to be breached. I explained this concept earlier in the chapter when reviewing dynamic analysis techniques. With this concept in mind, after validating all systems within contact of any infected system, you will need to run a network-wide scan for any threat that was found during the incident response. You can do this using the hash search technique previously covered or behavior signatures developed as the associated malware is analyzed. [Figure 8-24](#ch08.xhtml#ch08fig24) represents the recommended approach to responding to impacted systems during an incident response.

![FIGURE 8-24 Order of Systems to Address](Images/08fig24.jpg)

**FIGURE 8-24** Order of Systems to Address

Containment needs to include a method to prevent the threat from spreading. [Chapter 2](#ch02.xhtml#ch02) covered different types of segmentation techniques. I recommend complete isolation if possible, as systems on the same network segment can spread malware. Isolation of network resources should also be enforced to prevent the malware from sending data off the network. This action can alert the adversary that their malware has been identified, which means you want to execute swift containment of all threats to avoid the adversary adjusting their attack plan based on being alerted that the malware is being contained.

#### Eradication Playbook
