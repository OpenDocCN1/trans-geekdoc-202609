
The most difficult case is what are called **Advanced Persistent Threats (APTs)**, which are attack preparations that are potentially serious but happen really infrequently, perhaps weeks or months apart. These are widely believed to originate from states, patiently accumulating information about potential targets. They are difficult to notice because each individual step seems fairly inconsequential and the sequence is hard to detect because of the time gaps between them.

It's natural to ask why computer systems aren't all as well defended as they can be. We touched on this in [Chapter 4](#04chap_04.xhtml)—the behavior of pipes is practically impossible to update; and nodes are updated on a regular schedule, typically monthly or biweekly.

However, many systems are not even updated to the current best level because of a concern that updates will break the ongoing operation of nodes. A business may not be able to afford the downtime that could be triggered by an update that interacts poorly with their core revenue-generating systems. Such businesses may trial each update in a walled-off environment to judge if its deployment will cause issues, and this process takes time. There may therefore be organizations whose update state lags behind what it could be by months, and these yet-to-be-updated systems are natural targets for attackers.

There are also a surprisingly large number of systems that are unattended, and have been forgotten by their owners. Such systems may never be updated, and so represent serious vulnerabilities for their organizations. Some systems, notably Internet of Things devices and routers are impossible (or extremely time consuming) to update.

There are resource implications to keeping a large set of computers up to date, and so many organizations also find themselves forced to triage to keep their most critical systems best protected, and live with some level of risk for less-important systems. Organizations can get a perspective on their level of risk using **attack graphs**. These represent how easy Internet-facing systems are to attack, and then transitively assess how easy the systems one step away from the Internet are to attack, and so on, based on the versions of all of the software that they have installed. An attack graph can indicate to systems staff where the most cost-effective interventions can be made to protect the overall system. (An attack graph is also what an attacker would most like to have, and is attempting to construct implicitly by surveillance.)

Defenders can also keep track of incidents that are indicators of surveillance or early-stage attacks. One way to do this is to look at the logs which record many activities on systems. This is not done as often as it probably should be because logs are very detailed (and grow quickly) so it is hard to pick out anomalous activities that might signal probing or attack preparation. Tools to partially automate this step are becoming available. Nevertheless it is still true that logs are often only looked at afterwards to work out how an attack happened and to attribute it, rather than as a real-time defensive tool.

Some organizations set up systems called **honeypots**, systems that are designed to look like attractive targets but actually contain nothing of real value. Honeypots can be watched by defenders more carefully than other computers, so that they act as tripwires, notifying defenders of a potential attack. Their other advantage is that a defender can examine the attacker's strategy as it is revealed in the attack on the honeypot, and so see how that attacker might approach other computers in the organization.

In organizations where security is paramount, computers may have their entire software and systems reloaded every day. This means that an attacker has a very limited time to exploit a successful attack, and cannot leave behind a backdoor for further attacks.

## 6.6 Recovery

When a successful attack has taken place, a defender has to carry out a number of tasks to recover, and perhaps to deal with the attacker legally.

Obviously, the first phase is damage control. Something will have happened that causes the defender to realize that an attack has taken place. The defender must try to work out what the damage to the organization has been and remediate it if possible. The defender will then need to work out how the attack was carried out. This will often require careful analysis of logs to find the traces of the attack.

The second phase is to fill the holes that allowed the attack to happen. This might be straightforward if the weakness was the lack of updates but might be more difficult if the attack used a zero-day mechanism because the defender cannot easily tell exactly what happened.

The third phase is to work out how (if possible) to attribute the attack, and perhaps take retribution. Attribution is difficult in principle because of the ease with which the source of an attack can be hidden behind spoofed source addresses. In practice, however, attackers are careless and sometimes unaware of what is collected about activities, and it may be possible to infer, with some assurance, who carried out an attack. Curiously developers seem unable to resist the temptation to sign their work when they build malware, and this has often helped with attribution.

When it comes to retribution, organizations such as businesses can try to involve law enforcement. This tends not to work well because police forces do not have large numbers of employees with the skills necessary to understand an attack, and neither do courts.

Governments tend to be proactive about attribution because they need to understand how attacks fit into larger international relationships, and may resort to active cyber operations as a form of cyber deterrence. This is a rapidly developing area.

# Chapter 7: Application Security

Most applications communicate by using the protocols we have already discussed, notably `TCP/IP`. However, there are protocols that allow particular apps running on different systems to communicate with one another at a higher level of abstraction, that is, treating the entire pipe system as a communication mechanism without having to pay attention to the details of how it works.

Working at this higher level of abstraction also makes it easier to see that certain types of traffic flows should not be allowed. This done by **intrusion detection systems**, which are analogous to firewalls, but operate within individual nodes, rather than in the pipes. Because of where they are, they can better see which patterns of traffic flows make sense (to and from running apps) and which do not, and can block those that don't make sense. Because they run within nodes they also have the resources to examine traffic in more detail and with longer deadlines, so they can do a more thorough job.

We now consider two of these application-layer systems.

## 7.1 Email

Sending an email requires the sender's email client to send the message to its local email server. This email server must then transfer the message to an email server at the destination, and this server passes it on to the email client belonging to the receiver. The communication mechanism between the two servers uses an application-layer protocol called the **Simple Mail Transfer Protocol (SMTP)**. Email was an early use of a network, and this protocol dates back to the days of trusted networks. Security was not a consideration when it was defined, because email was a way to move simple text from a sender to a receiver.

Email has since been overloaded with many other functionalities such as moving arbitrary files as attachments, or organizing meetings. Security mechanisms, minimal to start with, have not kept up with all this new functionality.
