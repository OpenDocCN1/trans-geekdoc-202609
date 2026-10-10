
# Brute Forcing Parameters with Burp Suite Intruder

We want to brute force through all the different parameter values to see which pages exist and which pages do not. Since we already have our traffic flowing through Burp, we can go to the **Proxy** tab and to your **History** tab. You will see all your past requests there. Right-click on that last request and click **Send to Intruder**.

![](images/00092.jpeg)

**Figure 55 - Sending Request to Intruder**

Your **Intruder** tab at the top menu bar will light up, and then click that **Intruder** tab. Move to the **Positions** tab and you’ll see a bunch of highlighted text. Since I am only testing one parameter at this time, I’ll click the **Clear** button first, highlight just the `2` value (as it is the only one I want to fuzz), and click the **Add** button on the right side (Figure 56). This tells Burp to only fuzz whatever value is fed into the `ID` GET parameter and that parameter will now be yellow.

There is one other configuration selection and it’s the **Attack type**. In this case, I’ve left it at the default type of **Sniper**. You should spend a quick second and review each of the different types of attacks on Burp Suite’s site: <http://portswigger.net/burp/help/intruder_positions.html>.

![](images/00093.jpeg)

**Figure 56 - Burp Payload Positions**

Move over to the **Payloads** tab (still within the **Intruder** tab) and click the **Load** button. In this case, I am only loading a list of numbers from 1-100, but you can add a list of anything. If I know the parameter needs to be manipulated based on what I am interacting with (could be a database or an LDAP queries), I’ll import a list of those fuzzed parameters. It’s really up to you to figure out which types of tests you should fuzz. From our setup phase, you should have a great fuzzing list located under `/opt/SecLists/` on your Kali machine.

![](images/00094.jpeg)

**Figure 57 - Burp List**

Once you have your list imported, you’ll need to kick off the Intruder attack. At the top menu bar, go to **Intruder** > **Start attack**. After you start the attack, a new **Intruder Attack** window will pop up and Burp will start trying all the parameter requests.

![](images/00095.jpeg)

**Figure 58 - Starting Brute Forcing in Burp Suite**

![](images/00096.jpeg)

**Figure 59 - Burp Suite Results**

As the requests start populating, how can you tell if a site is different based on parameter injection? Well, the easiest way to tell is by the length of the source code on that page when that string is injected. If the source code length is different from a standard baseline, this informs us that there are changes to the page.

If we look at the results from the test above we see that from the parameter values we are injecting from 5 to 26, the page content length is 509. This source length of 509 is now our baseline for testing. If we go through and look at all the responses of all the pages that are not 509 in length, we see that request 27, with a length of 456, gives us the password: `dont hack me` (image above).

You can also try manipulating anything in the original request. Try testing cookie values, `GET`/`POST`/`HEAD` parameters, user-agent strings, and other possible vulnerable fields.

![](images/00097.jpeg)

## Functional Testing Importance

I want to stress one additional aspect when testing an application. As this book is really just giving a high level view into web application testing, functional testing is really where you make your money. When I say functional testing, I see it as horizontal/vertical user rights testing, application flow testing, and making sure things work as they should. For example:

*   Testing that users aren’t able to see other user’s sensitive data.
*   Regular users can’t access administrative pages.
*   Users can’t change data values of other users.
*   Workflows cannot be modified outside their intended flow.
*   If you are interested in learning more you can visit <https://www.owasp.org/index.php/Web_Application_Penetration_Testing>.

This is where successful testers spend a majority of their time. Anyone can run scans, but if you are an effective and efficient manual tester, you are leagues above the norm.

![](images/00098.jpeg)

## Network Penetration Testing Overview

In a network level penetration test, time is of the essence. You need to have a solid understanding of the underlying infrastructure, application, and possible vulnerabilities. This chapter should have helped you understand a high level overview of vulnerabilities, how to identify them, and what type of impact they might have if that vulnerability is not resolved.

Web vulnerabilities will probably be the most common vulnerability you’ll identify on an external penetration test. You should now be able to demonstrate how to take advantage of these issues in a simple and quick manner.

![](images/00099.jpeg)

# Lateral Movement and Privilege Escalation

A lateral pass play is used when you can’t seem to move forward. You might be on a network, but without privileges or account credentials, you’d normally be stuck on a box. As a tester, where you start to standout is when you are able to move through the network and gain access to domain administrative accounts. One thing I stress as a penetration tester is that this shouldn’t be your only goal. It is just as important to be able to identify where sensitive data is being stored and gaining access to those environments. This might require pivoting through essential employees and understanding how the corporation segments their data.

This section will be focused on moving through the network and trying to go from becoming a limited user all the way to owning the whole network. We will cover such topics as starting without credentials, proxying through hosts, having limited domain credentials, and then having local/domain credentials.

![](images/00100.jpeg)

## Starting Without Credentials

Let’s say that you are on the network, but you don’t have any credentials yet. Maybe you cracked their WPAv2 Personal Wi-Fi password or popped a box that wasn’t connected to the domain. I might first turn on `tcpdump` to listen passively, identify the network, find the domain controllers, and other passive types attacks. Once I feel like I have an understanding of the local network, I’ll start compromising systems using a variety of attacks specified in the next few sections.

![](images/00101.jpeg)

### Responder.py (Kali Linux)

One tool that has helped me in to gain my first set of credentials is called `responder.py`. Responder is one of the first tools that listens and responds to **LLMNR** (Link Local Multicast Name Resolution) and **NBT-NS** (NetBIOS over TCP/IP Name Service).

The other vulnerability Responder actively takes advantage of is the **WPAD** vulnerability. You can read more on a Technet article here: MS12-074 - Addressing a vulnerability in WPAD’s PAC file handling (<http://blogs.technet.com/b/srd/archive/2012/11/13/ms12-074-addressing-a-vulnerability-in-wpad-s-pac-file-handling.aspx>). The basics are that when a browser (IE or network LAN settings) is set to automatically detect settings, the victim host will try to get the configuration file from the network.

![](images/00102.jpeg)

**Figure 60 - Automatically Detect Settings**

As the attacker, since we are on the same network as our victims, we can respond to Name Resolutions and inject our own PAC file and proxy all web traffic. This way we can also force the user to authenticate against our SMB servers. You might ask, “Why is this important”? If we can get the victim host to authenticate against our SMB servers, we can request their NTLM challenge/response hashes without alerting the victim that anything is misconfigured. If the user is already authenticated to the domain, they will try to use those cached credentials to authenticate against our servers.
