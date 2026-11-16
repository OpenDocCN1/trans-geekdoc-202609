# FIGURE 4.10 Job requirements for a network security engineer

+   - At least 5 years of experience with administration and implementation of IT security infrastructure(mainly CheckPoint, PaloAlto, ForeScout, ISA/TMG, F6)
+   - At least 5 years of experience with networking mainly Cisco switches, routers, Wif as well as F5 load balancers
+   - Knowledge of AWS/ Azure/ Google/ 365 cloud Infrastructure is recommended
+   - Knowledge of networking protocols such such as TCP/IP, BGP/OSPF/ISISec, etc.
+   - A deep understanding of monitoring systems and procedures (SolarWinds Orion, PRTG, SNMP)
+   - Knowledge of authentication protocols such as OAuth, SAML, RADIUS, etc.
+   - Unified communication knowledge – an advantage

We don't have to limit ourselves to the web interface, though, since it can be tedious to keep typing things and flicking through pages. Instead, we can use the program InSpy. This is available as a package that can be installed on Kali Linux. It’s a Python script, though, that can be run from anywhere if you want to download it to another system. Running InSpy, we can gather job listings based on a list of technology requirements. If you provide a text file with the technology you want to look for, InSpy will look for jobs at a company you specify that match those technologies.

Beyond jobs, though, we can use LinkedIn to harvest information about people. There are a couple of reasons to look up people. One is just to get some names and titles that you may use later on. Another is that even if job descriptions don't have information about technology, when people post their job responsibilities, they very often do. You can also get details about their certifications. Someone with a load of Cisco certifications, for example, is probably employed at a company that has a lot of Cisco equipment. Don’t overlook non-technical roles either. Anyone may provide a little insight into what you may find in the organization. You may get information about telephone systems and document management systems that the company uses, even if the employee isn't an administrator.

Again, we turn to InSpy for a little help here. We provide a text file with titles in it. Providing partial titles works. The text file I am using for our little foray here just has the words engineer, editor, and analyst in it. You’ll see in the following code that the titles returned include more words than just those. This means you don’t have to be exact about the titles you are looking for. You do have to provide a file, though. InSpy won’t just search blindly through LinkedIn for every person at a particular company. In addition to the text file, you tell InSpy what the company you are looking at is. You can see the command line used to call the program as well as a partial listing of people. This particular search returned 59 people, so only some of them are shown here just to give you a sense of the types of responses you can get.

# InSpy Results from an Employee Search

```
$ ins --empspy title-list-small.txt Wiley

InSpy 2.0.3

2018-07-02 16:00:52 59 Employees identified
```