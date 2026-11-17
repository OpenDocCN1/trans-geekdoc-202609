# # Homepage Hijacking

The function of these attacks is to change your browser’s homepage to point to the attacker’s site. There are two forms of hijacking:

+   * **Exploiting a browser vulnerability to reset the homepage**—Many types of active content can change the browser’s homepage, often without the user’s permission. Even without resorting to covert means, it is easy to convince a user to select an action that does more than he or she expects. Just because you click a button that says “Remove Infected Programs from My Computer” doesn’t mean that’s the action that will occur.

+   * **Covertly installing a browser helper object (BHO) Trojan program**—This Trojan contains the hijacking code. Once a BHO executes, it can change the browser’s homepage back to the hijacker’s desired site. Typically, hijacker programs put a reference to themselves into the operating system’s startup procedures. That way the hijacker runs every time the computer reboots. If you try to change any of these settings, the hijacker repeatedly changes them back until you find and remove the hijacking software.

# # Webpage Defacements

The term **web defacement** or **web graffiti** refers to someone gaining unauthorized access to a web server and altering the index page of a site on the server. Usually the attacker exploits known vulnerabilities in the target server and gains administrative access. Once in control, the attacker replaces the original pages on the site with altered versions. For example, FIGURE 11-13 shows a defaced *New York Times* webpage.

Typically, the defacement represents graffiti. Most security practitioners consider this form of attack to be merely a nuisance. The potential for embedding malicious active content code such as viruses or Trojans into the website does exist, however. Code Red, for instance,

# # How Can Attackers Attack Web Applications?

Applications that users access using a web browser are called **web applications**. Most people just think of web applications as websites, but they really are far more powerful. A web application generally provides access to data in a database and uses those data to provide some service to the user. For example, online shopping sites are really web applications. Attackers often target web applications since the application provides access to vast amounts of data. One method attackers use is called **session hijacking**. Session hijacking is an attack in which the attacker intercepts network messages between a web server and a web browser. It extracts one or more pieces of data, most commonly a session ID, and uses that to communicate with the web server. The attacker pretends to be an authorized user by taking over the authorized user’s session. The technique used when the attacker masquerades as an authorized user is called **header manipulation**. The attacker creates an HTTP message for the web server but changes (manipulates) the HTTP header to include the intercepted session ID. When the web server receives the altered HTTP message, it thinks the attacker is an authorized user. This is an effective attack for web applications that fail to authenticate each request.