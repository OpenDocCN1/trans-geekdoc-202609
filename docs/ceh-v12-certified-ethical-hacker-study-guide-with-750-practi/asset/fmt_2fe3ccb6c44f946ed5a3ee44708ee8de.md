
This only gives us the operating system and the web server. These days there is far more technology being used in websites. Static pages are written in HTML, but it's far more likely that you'll be running up against a dynamic site. This means you may find a site written in the PHP or Java programming language. The language itself isn't enough to provide the deep functionality needed by a robust web application. Instead, website programmers are apt to use frameworks. The frameworks can have vulnerabilities, as exhibited by the Experian data breach, which used a vulnerability in the Spring framework used by Java‑based applications.

Back to the land of web browser plugins we go. One that is really good is Wappalyzer. Wappalyzer can be added to both Chrome and Firefox. When you visit a website, Wappalyzer will provide a list of technologies it identifies. This may include the web server, programming frameworks, ad networks, and tracking technology. It's not always successful in identifying everything. Going to `www.google.com` turns up the Google web server and an analytics framework. However, visiting CNN turns up a lot of different technologies, some of which you can see in [Figure 4.16](#c04.xhtml#c04-fig-0017). What we don't get there is the web server being used by CNN. We will take what we get, though, considering all the other technologies in use on the site.

![FIGURE 4.16 Wappalyzer for technology](images/c04f016.png)

[**FIGURE 4.16**](#c04.xhtml#R_c04-fig-0017) Wappalyzer for technology

There are other ways you can dig into web pages and the technologies used. One of them is Firebug. It's available on Firefox, though there is also Firebug Lite that's available in Chrome. Firebug Lite doesn't have quite the same capabilities as the full Firebug. However, on Chrome, Google has provided the developer tools. Using either the Chrome developer tools or Firebug, you can perform a deep investigation of the page you are looking at. To begin with, you can look at the Document Object Model (DOM) and all of its components. You can also select different HTML elements in the page and identify styles and properties applicable to that section. [Figure 4.17](#c04.xhtml#c04-fig-0018) shows a portion of the information that you can get using the Chrome developer tools. The page being inspected here is a Google search page. Using a tool like this, you can get a better understanding of how the page operates by looking at all the elements of the page and how they relate to one another.

 ![FIGURE 4.17 Chrome developer tools](images/c04f017.png)

[**FIGURE 4.17**](#c04.xhtml#R_c04-fig-0018) Chrome developer tools

Websites are complex creatures. The Chrome developer tools and Firebug are capable of looking at only a page at a time. You'd have to dig through every page, one at a time, to investigate them and their capabilities. You may find it easier to mirror the website so you could look at it offline. With it stored locally, you could look at the pages as many times as you would like without needing to issue repeated requests to the remote server. While the requests aren't likely to raise any eyebrows and aren't even likely to be noticed, you are leaving tracks behind. One tool you can use to mirror the website is HTTrack. In the following code, you can see the results of running HTTrack to mirror a website. The program will essentially perform a spider on the remote site, storing the results in the directory provided.

  **Mirroring Sites with `httrack`**

```
$ httrack

 Welcome to HTTrack Website Copier (Offline Browser) 3.49-2+libhtsjava.so.2 Copyright (C) 1998-2017 Xavier Roche and other contributors
 To see the option list, enter a blank line or try httrack --help
  
 Enter project name :MySite
  
 Base path (return=/root/websites/) :
  
 Enter URLs (separated by commas or blank spaces) :http://www.domain.com
  
 Action:
 (enter)    1    Mirror Website(s)
    2    Mirror Website(s) with Wizard
    3    Just Get Files Indicated
    4    Mirror ALL links in URLs (Multiple Mirror)
    5    Test Links In URLs (Bookmark Test)
    0    Quit
 : 1
  
 Proxy (return=none) :
  
 You can define wildcards, like: -*.gif +www.*.com/*.zip -*img_*.zip
 Wildcards (return=none) :
  
 You can define additional options, such as recurse level (-r<number>),
 separated by blank spaces
 To see the option list, type help
 Additional options (return=none) :
 
```

Once you have the HTML, you can do anything you want with it. You can make changes, review all the scripts that are included in the pages, and review the pages as you need to. Not all technology is in the website, though. Organizations have a lot of other technology that can generally be mined using a variety of tools and techniques.

## Technology Intelligence

Ultimately, your goal as an ethical hacker is to identify vulnerabilities within the organization you are working for. While web interfaces are an attractive place to play and look for vulnerabilities, considering how much sensitive data can be available through web interfaces, it's not the only place to look for vulnerabilities. However, you can still make use of websites to continue to explore the bounds of technology within your target company. So far, we've identified job sites and some social networking sites in order to gain intelligence about technology in use at a target. Beyond that, we can look at a couple of other areas. The first is to help really focus our web searches using Google dorks, also known as Google hacking. Additionally, we can look for devices that are part of the so‑called Internet of Things (IoT).

### Google Hacking

Google hacking is an important skill to have. It will improve the search responses, saving you a lot of time clicking through pages that aren't especially valuable. Once you know some of the keywords that can be used to really narrow your searches, you'll save time and become more efficient. The Google hacking techniques will help you to identify technology and vulnerabilities. In addition to Google hacking techniques, there is the Google hacking database, which is a collection of Google dorks that have been identified by someone as a way to search for a number of things. A dork is a string using Google keywords, designed to search for useful responses.

First, the Google keywords. If you've been using search engines for a long time, you may be familiar with the use of quotation marks and Boolean terms to help ensure that you are getting the right strings in your responses. In addition to those, Google uses positional keywords. You may, for instance, want to look only in the URL for a particular string. To search in the URL, you would use `inurl` as in the example, `inurl:index`. This example would find pages that included the word index anywhere in the URL. This might typically be a page like `index.html`, `index.php`, or `index.jsp`. If you wanted to ignore the URL and only search in the text, you could use the keyword `intext.`

Since you are working for an organization, you have one domain or maybe a small handful of domains. This means you will, at some point, want to search only within those domains. To do that, you can use the `site` keyword. You may also want to limit your results to a single filetype, such as a portable document format (PDF) file or a spreadsheet. To limit your results to just one filetype, you would use the `filetype` keyword. Perhaps you are looking for all PDF documents about Windows 11 on Microsoft's site. [Figure 4.18](#c04.xhtml#c04-fig-0019) shows the search used for that (site:`Microsoft.com` filetype:pdf “Windows 11”) as well as a number of results.

 ![FIGURE 4.18 Google hacking results](images/c04f018.png)

[**FIGURE 4.18**](#c04.xhtml#R_c04-fig-0019) Google hacking results
