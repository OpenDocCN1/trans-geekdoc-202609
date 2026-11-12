another ding against it. But to be clear, an SPF pass doesn’t mean an email is or isn’t a malicious email. Sadly, today, most phishing emails pass SPF (and other DMARC checks). All it means is that the claimed 5321 domain was or wasn’t the domain actually involved. More on this below.

Figure 7-10 shows an SPF pass on a real-world phishing email.

![](bbox=[0.1, 0.275, 0.85, 0.695])

FIGURE 7-10 An SPF pass on a real-world phishing email.

As Figure 7-10 shows, many phishing attempts claim to be from a particular domain and are from that claimed domain. SPF is not a phishing-detection service. It just checks to see if the 5321 email address domain claimed by the email is really where the email is from. Whether an email passes or fails an SPF check is just another tidbit of information for you to decide if the email is malicious or not.