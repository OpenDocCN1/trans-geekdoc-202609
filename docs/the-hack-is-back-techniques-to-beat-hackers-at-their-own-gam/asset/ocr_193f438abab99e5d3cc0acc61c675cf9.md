Note that the comments at the start of our wordlist were sent and interpreted with the # character, which is considered as an anchor. The anchor refers to a resource within the document served and does not change the activity presented on the webpage. The anchor does not get sent to the website either.⁵ Keep in mind that JavaScript-heavy single page applications do leverage information beyond the anchor to dynamically change and update the page.

To prevent the comments within the wordlist from being sent as anchors and fragments with fluff, we can provide the **-ic** switch to ignore comments. When applied to our previous ffuf command, we can see a much cleaner output which makes it pretty clear what items have been found so far.

![](bbox=[0.108, 0.267, 0.894, 0.565])

**FIGURE 3.43** Much cleaner output after ignoring wordlist comments with the -ic switch.

To search for file extensions, we can use the **-e** switch to provide a comma-delimited list of extensions that will be added to each line. Keep in mind the other file extensions from the **GoBuster** section and understand what technology is used on the server side. If we know what language the server is written in, we can intelligently guess various extensions to try and increase the likelihood of success. Adding the extensions to our command results in the command below:

```
ffuf -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http://ffuf.me/FUZZ -ic -e .php,.html,.txt
```

Rate-limiting is another feature of **ffuf**, where we can specify the maximum amount of requests per second allowed. This is an important requirement to ensure that we do not overwhelm the target and accidentally cause a denial of service. To enforce a rate limitation, use the **-rate** switch with a number of packets per second. To reduce activity to 50 requests a second, add the **-rate 50** to the command in use.

Just like the other tools discussed in this chapter, this only begins to touch on the full capabilities of the program. It is highly recommended to use and become very familiar with these tools, as