In fact, the actual steps for a PHP installation look something more like this:

+   1. Install and configure the various external libraries.
+   2. Install and configure your database platform.
+   3. Install and configure your Web server.
+   4. Install and configure PHP.

As you can see, it’s far from child’s play. To make matters a lot worse, the exact manner in which the preceding steps are accomplished varies, depending on your chosen operating system (UNIX or Windows), your chosen Web server (Apache, IIS, Zeus, etc.) and your chosen database platform (MySQL, PostgreSQL, MS SQL Server, Oracle, IBM DB2, Informix).

Presenting the lowdown on every possible permutation in this appendix would not only affect the number of trees required to produce this book, it would be madness, because there’s a very convincing argument for one particular combination over any others.

# # The Winning Platform

To be clear about something, this book is not about operating system wars. Those of you interested in the great Windows versus UNIX debate can find literally thousands of pages of well-considered, informed dialogue among the ever-rational and well-spoken denizens of Slashdot (www.slashdot.org).

However, we do proffer the following bold statement: “Windows is bad at being an Internet application server, just as UNIX is bad at being a workstation operating system.”

This is somewhat of a sweeping generalization, and there are exceptions to the rule, but tens of thousands of ISPs and big businesses in the United States alone can’t be wrong. Although Windows is frequently found in the corporate environment as an Exchange server or domain controller, it is UNIX that hosts Web sites and DNS, and routes mail at the SMTP level across the whole of the Internet. Similarly, although there are those who choose to use Linux with X window managers such as Enlightenment, Gnome, and KDE on their laptops, they represent a minority. Most people recognize that Windows excels on the desktop, while UNIX excels as a server environment.

We are acutely aware of the fact that UNIX is a trademarked name, and refers to a specific operating system that is not the GNU/Linux distribution that most of us use on a daily basis. What we mean by using the commonly known appellation UNIX is a POSIX-compliant operating system, such as the various GNU/Linux distributions, FreeBSD, OpenBSD, Solaris, and so on, sometimes collectively referred to as “nix systems. However, *nix isn’t readily pronounceable and GNU/Linux, FreeBSD, OpenBSD, Solaris, and so on, is a lot to type. Therefore, we have chosen to use UNIX.

The reasons for this distinction are really quite simple. The Windows interface is optimized for the desktop because it has undergone year after year of development with GUI desktop applications as a primary focus. Many thousands of hours have gone into researching and evolving the Windows user interface to make it intuitive and efficient. It’s not perfect, but it is better than what is offered by its UNIX counterparts.