identify it” provides little, if any, benefit to a paying client. Everything that we do needs to be given a specific impact to the organization.

Evaluating vulnerabilities is used to determine that the identified weakness can be exploited in a manner conducive to our objectives. At this point, we need to find out not only if the weakness can be attacked, but if it can be attacked in a manner that provides additional access for our objectives.

For example, let’s say we identify that a vulnerability exists on a webpage that shows there is no database connected when a user attempts to log in.

![](bbox=[0.321, 0.231, 0.679, 0.477])

**FIGURE 3.17** Screenshot of a web application that states that the MySQL server is not connected. Is this worth investigating further? How could this be weaponized?

This is a vulnerability, as it gives information about the web application, the technologies used, and the knowledge that others likely cannot log into this asset as well. An organization paying for an application test would certainly be interested in this information, a web application similar to this is likely old or forgotten infrastructure.

Consider also if this website were to be served over HTTP – most web application hacking tools would quickly classify this as a high risk. However, since there is no SQL server connected on the backend, this feels as though this may be a forgotten asset. Removing this asset is highly recommended, but it also could likely be downgraded from a high level of risk to either a medium or a low.

However, while this is a vulnerability on the target, it is extremely unlikely to provide tangible benefits for us to attack further. How can we exploit a login if there’s no database for the logins to check against? Is it possible to weaponize this for further access? Sure, there may be a social engineering aspect to reaching out and stating that you cannot log into a website, but who will even realize that the forgotten infrastructure is still running? Certainly, there are very limited technical exploits we can achieve against this target, and we should focus our efforts elsewhere.

# WEAPONIZATION

Once we’ve identified vulnerabilities that we know we can exploit, we now need to identify a way to create a tangible **IMPACT** with this weakness. Identifying the vulnerability is only the beginning. Creativity is heavily involved with weaponization, simply because there are so many ways that most exploits can be used.

For example, let’s consider a simple XSS vulnerability on a login page – so what if you can pull up an *alert()* box? Is that supposed to be bad?