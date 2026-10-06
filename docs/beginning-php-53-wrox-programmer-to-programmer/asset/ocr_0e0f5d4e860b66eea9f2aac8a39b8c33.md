# Chapter 10: Preserving State With Query Strings

As you can see, a cookie contains a number of pieces of information, summarized in the following table:

| Cookie Field | Description |
| --- | --- |
| name (for example

Although you can use the domain field to get the browser to send cookies back to other machines within the same domain, you can't use this trick to set cookies for sending to other domains. For example, if your Web site at www.example.com tries to set a cookie with a domain value of www.google.com, the cookie will be rejected by the browser.