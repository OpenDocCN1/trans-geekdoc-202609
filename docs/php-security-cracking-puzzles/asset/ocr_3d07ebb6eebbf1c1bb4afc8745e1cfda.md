# Part II: Solutions

The regular expressions in both scripts have the i and s modifiers. The i modifier specifies that the search should be case-insensitive. The s modifier is necessary for multiline constructions to be properly processed by the regular expression. The additional u modifier in the regular expression in Listing II.8.4 specifies the ungreedy search mode. The reason for this mode is that in the greedy mode .+ sequence in the regular expression will find the first occurrence of the <a> tag and the last occurrence of the </a> tag in the page, placing almost all of the page's contents into the sout[2] [$1] variable.

After the scripts have been successfully tested on the local file, the search.php file can be replaced with the Internet path to the page:

```
http://search.yahoo.com/search?p=PHP&sn=Yahoo%21+Search&fr=fp-tab-web-t&toggle=1&cop&ei=UTF-8
```

By doing this, the scripts will refuse to run. The reason for this is that Web developers often protect their resources by setting cookies, hard-wiring the HTML form of a session, or protecting the HTML form by checking the referrer. This sort of protection is not typical for search systems, which links may work regardless of whether or not the visitor's browser supports cookies or referrers Loading the page's source code using the script from Listing II.8.1 instead of the browser reveals that source codes loaded using PHP have not only different HTML code but also different page encoding. Thus, source codes loaded by a browser are encoded in the Unicode transformation format-8 (UTF-8), but those loaded using PHP have American Standard Code for Information Interchange (ASCII) encoding.

The reason for this mess is that even though UTF-8 encoding is specified in the request string, Web servers and the Yahoo search system go by the HTTP headers sent by the browser. Thus, headers like Accept, Accept-Language, User-Agent, and so on, specify the browser's preferences for a certain document format and language and indicate the browser version and the operating system used. The file_get_contents() function does not send any headers to the server, and the latter considers it to be a primitive browser not capable of processing UTF-8-encoded documents or supporting cookies.

Where HTML code is simplified by the Web application, the encoding may be changed by the server. Half of Internet sites encode pages requested by a browser in a different way than the same pages requested by a PHP script.

![](bbox=[0.085, 0.835, 0.205, 0.955])

NOTE