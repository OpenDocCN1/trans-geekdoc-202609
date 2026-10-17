
```text
(kali㉿kali)-[~]
$ ffuf -h
Fuzz Faster U Fool - v1.5.0 Kali Exclusive <3

HTTP OPTIONS:
-H        Header "-Name: Value-", separated by colon. Multiple -H flags are accepted.
-X        HTTP method to use
-b        Cookie data "NAME1=VALUE1; NAME2=VALUE2" for copy as curl functionality.
-d        POST data
-http2    Use HTTP2 protocol (default: false)
-ignore-body  Do not fetch the response content. (default: false)
-r        Follow redirects (default: false)
-recursion    Scan recursively. Only FUZZ keyword is supported, and URL (-u) has to end in it.
-recursion-depth  Maximum recursion depth. (default: 0)
-recursion-strategy  Recursion strategy: "default" for a redirect based, and "greedy" to recurse on all matches.
-replay-proxy  Replay matched requests using this proxy.
-sni      Target TLS SNI, does not support FUZZ keyword
-timeout  HTTP request timeout in seconds. (default: 10)
-u        Target URL
-x        Proxy URL (SOCKS5 or HTTP). For example: http://127.0.0.1:8080 or socks5://127.0.0.1:8080

GENERAL OPTIONS:
-V        Show version information. (default: false)
-ac       Automatically calibrate filtering options (default: false)
-acc      Custom auto-calibration string. Can be used multiple times. Implies -ac
-ach      Per host autocalibration (default: false)
```

**FIGURE 3.41** Truncated help information from ffuf. The help information has 95 lines in total, which is a lot of information to read, but important to understand.

To use ffuf, we need to provide at least two basic pieces of information, the wordlist used and the URL for fuzzing. For ffuf to understand where it needs to place fuzzing information, we also need to provide the string FUZZ at the location where we are testing. Its most basic form can be achieved with a command similar to the one below:

```bash
ffuf -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http://ffuf.me/FUZZ
```

```text
(kali㉿kali)-[~]
$ ffuf -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http://ffuf.me/FUZZ

       /'___\  /'___\           /'___\
      /\ \__/ /\ \__/  __  __  /\ \__/
      \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\
       \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/
        \ \_\   \ \_\  \ \____/  \ \_\
         \/_/    \/_/   \/___/    \/_/

v1.5.0 Kali Exclusive <3
________________________________________________

:: Method           : GET
:: URL              : http://ffuf.me/FUZZ
:: Wordlist         : FUZZ: /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt
:: Follow redirects : false
:: Calibration      : false
:: Timeout          : 10
:: Threads          : 40
:: Matcher          : Response status: 200,204,301,302,307,401,403,405,500

[Status: 200, Size: 1495, Words: 230, Lines: 40, Duration: 196ms]
# on atleast 2 different hosts [Status: 200, Size: 1495, Words: 230, Lines: 40, Duration: 197ms]
about                  [Status: 200, Size: 1229, Words: 136, Lines: 27, Duration: 197ms]
directory-list-lowercase-2.3-medium.txt [Status: 200, Size: 1495, Words: 230, Lines: 40, Duration: 200ms]
# Priority ordered case sensitive list, where entries were found [Status: 200, Size: 1495, Words: 230, Lines: 40, Duration: 195ms]
# This work is licensed under the Creative Commons
```

**FIGURE 3.42** Anchors showing fragment identifiers that do not change the information returned by the server; this clutters up the output from the tool.

Note that the comments at the start of our wordlist were sent and interpreted with the # character, which is considered as an anchor. The anchor refers to a resource within the document served and does not change the activity presented on the webpage. The anchor does not get sent to the website either.⁵ Keep in mind that JavaScript-heavy single page applications do leverage information beyond the anchor to dynamically change and update the page.

To prevent the comments within the wordlist from being sent as anchors and fragments with fluff, we can provide the **-ic** switch to ignore comments. When applied to our previous ffuf command, we can see a much cleaner output which makes it pretty clear what items have been found so far.

![](img/181571ad74cba0e6a2f38fcd2658651e_100_0.png)

**FIGURE 3.43** Much cleaner output after ignoring wordlist comments with the -ic switch.

To search for file extensions, we can use the **-e** switch to provide a comma-delimited list of extensions that will be added to each line. Keep in mind the other file extensions from the **GoBuster** section and understand what technology is used on the server side. If we know what language the server is written in, we can intelligently guess various extensions to try and increase the likelihood of success. Adding the extensions to our command results in the command below:

```bash
ffuf -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http://ffuf.me/FUZZ -ic -e .php,.html,.txt
```

Rate-limiting is another feature of **ffuf**, where we can specify the maximum amount of requests per second allowed. This is an important requirement to ensure that we do not overwhelm the target and accidentally cause a denial of service. To enforce a rate limitation, use the **-rate** switch with a number of packets per second. To reduce activity to 50 requests a second, add the **-rate 50** to the command in use.

Just like the other tools discussed in this chapter, this only begins to touch on the full capabilities of the program. It is highly recommended to use and become very familiar with these tools, as uncovering hidden or forgotten files is an easy way to gain access to a system for an organization. Some additional fantastic resources on using ffuf are below:

- [http://ffuf.me/](http://ffuf.me/)
- [https://danielmiessler.com/study/ffuf/](https://danielmiessler.com/study/ffuf/)
- [https://coding.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html](https://coding.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)

## Python Libraries

There are certain times when we need to create a tool for our specific situation. There will be scenarios where the implementation of a web application is in such a way that an existing tool does not exist for us to use. In these instances, we will need to create our own tool out of Python or some other programming language to attack the item effectively.

One of the great things about modern programming is how many open-source libraries are available. If you’re looking to complete some type of task, such as making an HTTP request or performing a specific type of hashing, chances are that someone else has already created a library that can complete these functions. These already written functions are easily integrated open-source libraries that can be accessed, saving countless amounts of time on your end. Using programs such as **pip**, we can install a library that has already written code to help perform a specific action and utilize it within our program. For example, the **requests** library helps simplify HTTP requests and create a much more manageable way to programmatically integrate with our needs.

The **pip** program uses the Python Package Index (PyPI) at [pypi.org](https://pypi.org). This is a location where many exceptional libraries are hosted along with links to their documentation. Updates are pushed to PyPI as well, where the **pip** program can be used to update the library as needed.

![](img/181571ad74cba0e6a2f38fcd2658651e_101_0.png)

**FIGURE 3.44** [Pypi.org](https://pypi.org) website which hosts many useful Python libraries.
