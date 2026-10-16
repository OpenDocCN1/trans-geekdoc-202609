
<x0.1215><y0.1492>Script code reflected to the browser.<x0.5586><y0.1562><class_Text>

<x0.1215><y0.1688>There are many more ways to exploit XSS, such as those requiring user interaction via the JavaScript `onmouseover` function.<x0.5586><y0.1812><class_Text>

<x0.1215><y0.1938>As with SQL injection, you really need to use an automated scanner to check for XSS.<x0.5586><y0.2062><class_Text>

<x0.1215><y0.2188>Both Netsparker and Acunetix Web Vulnerability Scanner do a great job of finding XSS, but they tend to find different XSS issues — a detail that highlights the importance of using multiple scanners when you can.<x0.5586><y0.2469><class_Text>

<x0.1215><y0.2695>![Figure 15-6:](#c15.xhtml#c15-fig-0006) shows some sample XSS findings in Acunetix Web Vulnerability Scanner.<x0.5586><y0.2828><class_Text>

<x0.1215><y0.3055>![FIGURE 15-6:  Using Acunetix Web Vulnerability Scanner to find cross-site scripting in a web application.](images/9781119485476-fg1506.png)<x0.5586><y0.3188><class_Image>

<x0.1215><y0.3453>![FIGURE 15-6:](#c15.xhtml#rc15-fig-0006)  Using Acunetix Web Vulnerability Scanner to find cross-site scripting in a web application.<x0.5586><y0.3586><class_Text>

<x0.1215><y0.3859>![tip](images/tip.png)<x0.5586><y0.3984><class_Image>

<x0.1215><y0.4109>Another web vulnerability scanner that's good at uncovering XSS that many other scanners won’t find is AppSpider (formerly NTOSpider) from Rapid7 ([`https://www.rapid7.com/products/appspider`](https://www.rapid7.com/products/appspider)).<x0.5586><y0.4336><class_Text>

<x0.1215><y0.4462>In my experience, AppSpider works better than other scanners at performing authenticated scans against applications that use multifactor authentication systems.<x0.5586><y0.4594><class_Text>

<x0.1215><y0.4719>AppSpider should be on your radar.<x0.5586><y0.4844><class_Text>

<x0.1215><y0.4973>Never forget: When it comes to web vulnerabilities, the more scanners, the better! If anything, someone else may end up using one of the scanners that you don’t use.<x0.5586><y0.5105><class_Text>

### Countermeasures against input attacks

<x0.1215><y0.5234>Websites and applications must filter incoming data.<x0.5586><y0.5367><class_Text>

<x0.1215><y0.5492>The sites and applications must ensure that the data entered fits within the parameters that the application is expecting.<x0.5586><y0.5625><class_Text>

<x0.1215><y0.5750>If the data doesn’t match, the application should generate an error or return to the previous page.<x0.5586><y0.5875><class_Text>

<x0.1215><y0.5992>Under no circumstances should the application accept the junk data, process it, and reflect it to the user.<x0.5586><y0.6125><class_Text>

Secure software coding practices can eliminate all these issues if they’re critical parts of the development process.<x0.1215><y0.6188> Developers should know and implement these best practices:<x0.5586><y0.6312><class_Text>

*   Never present static values that the web browser and the user don’t need to see.<x0.5586><y0.6445><class_List-item>

<x0.1484><y0.6516>Instead, this data should be implemented within the web application on the server side and retrieved from a database only when needed.<x0.5586><y0.6648><class_Text>

*   Filter out `<script>` tags from input fields.<x0.5586><y0.6672><class_List-item>

*   Disable detailed web server and database-related error messages if possible.<x0.5586><y0.6805><class_List-item>

### Default script attacks

<x0.1215><y0.6984>Poorly written web programs, such as Hypertext Preprocessor (PHP) and Active Server Pages (ASP) scripts, can allow hackers to view and manipulate files on a web server and to do other things they’re not authorized to do.<x0.5586><y0.7117><class_Text>

<x0.1215><y0.7242>These flaws are also common in the content management systems that developers, IT staff, and marketing professionals use to maintain a website’s content.<x0.5586><y0.7375><class_Text>

<x0.1215><y0.7500>Default script attacks are common because so much poorly written code is freely accessible on websites.<x0.5586><y0.7633><class_Text>

<x0.1215><y0.7758>Hackers can also take advantage of various sample scripts that install on web servers, especially older versions of Microsoft’s IIS web server.<x0.5586><y0.7891><class_Text>

<x0.1215><y0.8156>![warning](images/warning.png)<x0.5586><y0.8281><class_Image>

<x0.1215><y0.8406>Many web developers and webmasters use these scripts without understanding how they work or without testing them, which can introduce serious security vulnerabilities.<x0.5586><y0.8531><class_Text>

To test for script vulnerabilities, you can peruse scripts manually or use a text search tool (such as the search function built into the Windows Start menu or the Find program in Linux) to find any hard-coded usernames, passwords, and other sensitive information.<x0.5586><y0.8664><class_Text>

Search for *admin*, *root*, *user*, *ID*, *login*, *signon*, *password*, *pass*, *pwd,* and so on.<x0.5586><y0.8797><class_Text>

Sensitive information embedded in scripts is rarely necessary and is often the result of poor coding practices that give precedence to convenience over security.<x0.5586><y0.8938><class_Text>

### Countermeasures against default script attacks

<x0.1215><y0.9117>You can help prevent attacks against default web scripts as follows:<x0.5586><y0.9250><class_Text>

*   Know how scripts work before deploying them within a web environment.<x0.5586><y0.9258><class_List-item>

*   Make sure to remove all default or sample scripts from the web server before using them.<x0.5586><y0.9383><class_List-item>

*   Keep any content management system software updated, especially WordPress, as it tends to be a big target for attackers.<x0.5586><y0.9516><class_List-item>

    ![remember](images/remember.png)<x0.5586><y0.9641><class_Image>

<x0.1215><y0.9766>Don’t use publicly accessible scripts that contain hard-coded confidential information. They’re security incidents in the making.<x0.5586><y0.9891><class_Text>

*   Set file permissions on sensitive areas of your site/application to prevent public access.<x0.5586><y0.9973><class_List-item>

### Unsecured login mechanisms

<x0.1215><y0.1008>Many websites require users to log in before they can do anything with the application.<x0.5586><y0.1021><class_Text>

<x0.1215><y0.1034>These login mechanisms may not handle incorrect user IDs or passwords gracefully, divulging information that an attacker can use to gather valid user IDs and passwords.<x0.5586><y0.1047><class_Text>

To test for unsecured login mechanisms, browse to your application, and try these methods of logging in:<x0.5586><y0.1047><class_Text>

*   Use an invalid user ID with a valid password.<x0.5586><y0.1060><class_List-item>

*   Use a valid user ID with an invalid password.<x0.5586><y0.1073><class_List-item>

*   Use an invalid user ID with an invalid password.<x0.5586><y0.1086><class_List-item>

After you enter this information, the web application probably will respond with a message similar to `Your user ID is invalid` or `Your password is invalid`.<x0.5586><y0.1100><class_Text>

Or the web application may return a generic error message, such as `Your user ID and password combination is invalid`, and return different error codes in the URL for invalid user IDs and invalid passwords, as shown in [Figures 15-7](#c15.xhtml#c15-fig-0007) and [15-8](#c15.xhtml#c15-fig-0008).<x0.5586><y0.1113><class_Text>

![ FIGURE 15-7:  The URL returns an error when an invalid user ID is entered.](images/9781119485476-fg1507.png)<x0.5586><y0.1126><class_Image>

<x0.1215><y0.1152>![FIGURE 15-7:](#c15.xhtml#rc15-fig-0007)  The URL returns an error when an invalid user ID is entered.<x0.5586><y0.1165><class_Text>

![ FIGURE 15-8:  The URL returns a different error when an invalid password is entered.](images/9781119485476-fg1508.png)<x0.5586><y0.1179><class_Image>

<x0.1215><y0.1205>![FIGURE 15-8:](#c15.xhtml#rc15-fig-0008)  The URL returns a different error when an invalid password is entered.<x0.5586><y0.1218><class_Text>

Either situation is bad news. because the application is telling you not only which parameter is invalid, but also which one is *valid.* Malicious attackers now know a good username or password, so their workload has been cut in half! If they know the username (which usually is easier to guess), they can write a script to automate the password-cracking process, and vice versa.<x0.5586><y0.1231><class_Text>

You should also take your login testing to the next level by using a web login cracking tool such as Brutus ([`www.hoobie.net/brutus/index.html`](http://www.hoobie.net/brutus/index.html)), as shown in [Figure 15-9](#c15.xhtml#c15-fig-0009). Brutus is a simple tool that can be used to crack HTTP and form-based authentication mechanisms through dictionary and brute-force attacks.<x0.5586><y0.1244><class_Text>

![ FIGURE 15-9:  The Brutus tool tests for weak web logins.](images/9781119485476-fg1509.png)<x0.5586><y0.1257><class_Image>

<x0.1215><y0.1283>![FIGURE 15-9:](#c15.xhtml#rc15-fig-0009)  The Brutus tool tests for weak web logins.<x0.5586><y0.1296><class_Text>

![warning](images/warning.png)<x0.5586><y0.1309><class_Image>

<x0.1215><y0.1435>As with any type of password testing, this task can be long and arduous, and you run the risk of locking out user accounts. Proceed with caution.<x0.5586><y0.1448><class_Text>

An alternative tool for cracking web passwords is THC-Hydra ([`https://tools.kali.org/password-attacks/hydra`](https://tools.kali.org/password-attacks/hydra)).<x0.5586><y0.1461><class_Text>

Most commercial web vulnerability scanners have decent dictionary-based web password crackers, but none (that I'm aware of) can do true brute-force testing, as Brutus can.<x0.5586><y0.1474><class_Text>

As I discuss in [Chapter 8](#c08.xhtml), your password-cracking success is highly dependent on your dictionary lists.<x0.5586><y0.1487><class_Text>

Here are some popular sites that house dictionary files and other miscellaneous word lists:<x0.5586><y0.1500><class_Text>

*   [ `ftp://ftp.cerias.purdue.edu/pub/dict` ](ftp://ftp.cerias.purdue.edu/pub/dict)<x0.5586><y0.1513><class_List-item>

*   [ `https://packetstormsecurity.org/Crackers/wordlists` ](https://packetstormsecurity.org/Crackers/wordlists)<x0.5586><y0.1526><class_List-item>

*   [ `www.outpost9.com/files/WordLists.html` ](http://www.outpost9.com/files/WordLists.html)<x0.5586><y0.1539><class_List-item>

