
### Drones
You could use drones to fly over a facility and take video footage of the layout of the land and the building. This could help you understand weaknesses in physical security controls such as understanding the use of fences, guards, and exits.

### War driving
War driving is a wireless network attack technique where the attacker drives around using a wireless scanner such as `Kismet` to discover wireless networks and their characteristics, such as the operating channel, frequency, and security protocols configured.

### War flying
War flying is a form of war driving where the attacker uses low-flying private planes to scan areas for wireless networks. Using a wireless scanner such as `Kismet`, attackers fly at 1500 feet to discover a multitude of wireless networks.

### Footprinting
As you will learn later in this chapter, `footprinting` is another term for reconnaissance, which is discovering information about the intended target. You can use Internet resources to passively discover information about a company, or you can use scanning tools to actively discover information about systems running on the target network.

### OSINT
You can find a wealth of information about a company on the Internet, such as e-mail addresses as well as servers or devices connected to the Internet. Using Open Source Intelligence (OSINT) tools, you can easily retrieve information about a company that is available publicly. `Maltego` is an example of an OSINT tool that can collect e-mail addresses, files, phone numbers, DNS records, IP addresses, and geo-locations of assets for a company.

### Exercise Types
When performing a penetration test, you can use different types of testing. You could be performing the pentest so that you can attempt to hack into company assets (the goal of a red team), or maybe your goal is to see if the defensive team (that blue team) can detect that the attack is occurring and stop it. The following are the different security teams your company may employ:

#### Red team
The red team is the cybersecurity team that takes a methodological approach to attacking systems and attempting to bypass security controls. They are the attackers.

#### Blue team
The blue team is the cybersecurity team responsible for detecting an attack and protecting company assets by stopping the attack in its tracks. They are the defenders.

#### White team
The white team in cybersecurity is the team that oversees the security test and records the progress of both the red team and blue team and assigns the scores. The white team also reviews the security reports created by both the red team and the blue team to rate them based on their accuracy.

#### Purple team
A purple team in cybersecurity is a team that performs the functions of both the red team and the blue team.

![Image](exam.jpg)

**For the exam remember that the red team is responsible for performing attacks against the systems during a security test (the bad guys), while the blue team is responsible for detecting the attack and preventing a compromise (the good guys).**

### Understanding the Hacking Process
You perform a penetration test by following the hacking process, which is the methodology hackers follow when planning to attack an organization. The following sections outline the phases of the hacking process.

#### Profiling
The first phase of the hacking process is known as the reconnaissance phase or the profiling phase. In this phase, the hacker uses Internet resources to discover information about the organization. Here are some examples of ways the hacker collects information about the organization:

##### Web site
The hacker visits the organization's web site to get contact names, phone numbers, and e-mail addresses that they can use in a social engineering attack. The hacker also looks at job postings to learn what software the organization is running. For example, if the organization is looking for an Exchange Server administrator, chances are it is running Microsoft's e-mail server.

##### Google
The hacker will spend some time searching Google for specific information about the organization they wish to attack. In this step, the hacker will use Google keywords known as "Google hacks" to locate specific information about an organization. Examples of keywords you can use in Google to perform searches are `site:` to search a specific web site for content, `inurl:` to search for content in the URL of a web site, and `filetype:` to search for specific files such as PDFs or Word files. The following are some examples of Google searches you can use:

![Image](p0794-01.jpg)

##### Whois database
Another popular method that hackers use to discover information about an organization is to find out the IP addresses and DNS servers that an organization uses. To find this information, the hacker could use a whois database web site or program to do a search on the organization and obtain the list of IP addresses and DNS servers. An example of a web site that you can use for whois database searches is [https://www.whois.com/whois/](https://www.whois.com/whois/) (see Figure 20-5), or you can use the `whois` command-line tool in Kali Linux.

![Image](f0795-01.jpg)

**FIGURE 20-5**  
Using a whois site to locate company information

##### DNS profiling
Once the hacker has the IP addresses purchased by an organization, they are ready to move into the scanning phase next. But before leaving the profiling phase, the hacker will try to retrieve information from the organization's DNS server. The following code list shows the hacker using `dig` (a popular Linux program) to query DNS and retrieve information from DNS:

*   `dig www.certworld.loc` — This command reports the IP address of www.certworld.loc.
*   `dig certworld.loc MX` — This command finds the mail servers for certworld.loc.
*   `dig certworld.loc NS` — This command finds the DNS servers for certworld.loc.
*   `dig certworld.loc axfr` — This command attempts to view all DNS data for certworld.loc.

Note that 85 percent of the hacking process is spent on the profiling phase and on collecting information that the hacker can use in an attack.

![Image](exam.jpg)

**Reconnaissance performed in the profiling phase is known as `passive reconnaissance` because the hacker does not touch the organization's systems—the hacker is extracting information from public sources.**

### EXERCISE 20-2

![Images](video.jpg)

**Profiling an Organization**

In this exercise, you use some of the tools discussed in the profiling topic to learn information about an organization. You will do some whois database searching and some DNS profiling.

#### Performing a Whois Database Search
In this part of the exercise, you find information about my company, DC Advanced Technology Training, by using a whois database search. Although there are many web sites you can use, we will use the `whois` command in Kali Linux.

1.  Switch to the Kali Linux VM and start a terminal by clicking the second button on the application toolbar on the left.
2.  To search on dcatt.ca, type `whois dcatt.ca` and then press enter.
3.  Review the search result information and record as much of the following information as possible:

    Company name: _____________

    Contact person: _____________

    Phone number: _____________

    E-mail: _____________

    Address: _____________

    How current is this info? _____________

    Name servers: _____________

4.  Now try a graphical whois web site by launching a web browser and visiting [https://www.whois.com/whois/](https://www.whois.com/whois/). Type the following domain names in the search box and then click the Search button to view DNS information:
    *   [www.mheducation.com](http://www.mheducation.com)
    *   [www.dcatt.ca](http://www.dcatt.ca)
