# Chapter 10 - Certificate Transparency and Internet Archives 215

inherent vulnerability in it. Unless they code it, you can directly access resources from the dashboard or panel.

The Wayback Machine records websites at different states. If the Wayback Machine made a record of URL that is no longer in use or was open for a minute when it caught it, it can really be beneficial to knowing how an application works, or at least just a history of it.

The enum _wayback script was designed to give you a bunch of URLs that you might not have known about. It can show you URLs that existed and may not exist now. The script won't copy all of the functionality of a web application, but it does spider it.

Let's say they had a custom version of Drupal and a custom version of WordPress next. You're going to get both Drupal and WordPress URLs or URLs. There's a good chance that Java either files around or didn't set the routing correctly, or some other detail, and there's going to be technical debt then. Wayback not only finds its, but it also finds that was open probably shouldn't have been.

Let's use Bob's Web Store as an example. There's a good chance that Bob's Web Store has been around for 15 years, they didn't think about security until 10 years ago, and so those URLs were indexed and cataloged might still be there and very valid, now more secure.

It might be that 80% of them are more secure, but you might just find that one isn't—and can really make the difference. The script is designed to give you a resource of pages to look at.

Using it is really straightforward. All you do is point it at a specific host name or domain and it gives you the results from the Wayback, all parsed and nice and neat, so you don't have to page through anything and that makes it very easy to load into Burp, too.

# Enum Wayback

enum _wayback is a Ruby script that is part of the Metasploit framework. Since this is a book on investigations and OSINT, we really won't be digging too far into Metasploit or all of the amazing things you can do with it. If you haven't used Metasploit in the path (or maybe don't know what it is), Metasploit will be one of your primary tools when conducting a penetration test. Hundreds (if not thousands) of exploits and customizable modules are built into the tool, making it a necessity for any pen-tester.

For those of you versed in Metasploit, we can launch enum _wayback like this:

```
msf > use auxiliary/scanner/http/enum_wayback
```

To see our list of available options, we can type in options:

```
msf auxiliary(scanner/http/enum_wayback) > options
```