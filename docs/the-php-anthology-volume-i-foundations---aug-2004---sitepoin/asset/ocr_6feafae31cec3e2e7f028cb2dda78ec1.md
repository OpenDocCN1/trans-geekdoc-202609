# Appendix B: Hosting Provider Checklist

PHP, and, more generally, the LAMP combination of Linux, Apache, MySQL and PHP/Perl/Python, is widely available via literally thousands of Web hosts at very affordable prices. You can easily get quality Web hosting that will suit 90% of your needs for under $10 a month per site. That said, all PHP installations are not created equal, and depend largely on the configuration settings defined in php.ini as well as the extensions the host has installed for you. There are also a number of general issues relating to the amount of control you're given over your own environment, and these are important if you don't want big trouble later on.

This is a summary of the key issues you should investigate before paying for a hosting service. Contact potential providers and have them respond on each of these points. Follow up by asking for opinions from other people who know/have used the service in question. There are many online forums where you'll find people who are able to offer advice. Be aware, though, that the ratio of "knowledgable" to "ignorant" is stacked highly in favor of ignorance; gem up on technical detail so you're able to verify that the answers you were given were actually well-informed.

Some of the points I've provided here may seem a little extreme, but once you've been around the block a few times, you'll probably want to get value for your money, rather than spending your Saturday mornings fixing the problems your host made for you on Friday night.

# General Issues

+   - [ ] Require Linux and Apache (1.3)

From the point of view of performance and reliability, this is the best combination. Avoid any host using Apache 2.x (it's not yet completely stable with PHP). Ask for details of the Linux distribution. Although Red Hat and Suse are popular, you may find hosts using Debian (or, better yet, Rock Linux) know more about what they're doing.

+   - [ ] Does the host provide you with SSH access to the server?