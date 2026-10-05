Last, we can build the headers to force the browser to download the file rather than display it. Headers are fairly complicated. I'm not proclaiming to be an expert in assembling header content. However, if you're not sure what you need to include in a header you can send yourself an email with an attachment and view the source code. After a lot of searching on the Internet and coming up with methods that downloaded corrupted files I was finally able to piece together the following working code that outputs the file to the browser and keeps the cache cleaned up at the same time.

This part is required.

```
header("Pragma: public");

Expire the header immediately so it forces the browser to refresh the link instead of using the cache.

header("Expires: 0");

Expire the header today.

header("Last-Modified: .date(r)");

Force the browser to download the file from the server rather than the cache to get the latest copy of the file.

header("Cache-Control: must-revalidate
```