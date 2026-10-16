```
[soap]
; Enables or disables WSDL caching feature.
soap.wsdl_cache_enabled=1
; Sets the directory name where SOAP extension
will put cache files.
soap.wsdl_cache_dir="/tmp"
; (time to live) Sets the number of seconds while
cached file will be used
; instead of original one.
soap.wsdl_cache_ttl=86400
```

When developing a Web Service and maybe changing the WSDL, this is, of course, a no-brainer. Therefore, set soap.wsdl_cache_enabled to Off during development, but turn it on for production servers.

# Using Ajax

Wikipedia lists several dozen different meanings for the term Ajax, including a soccer team from the Netherlands, two figures in Homer's Iliad, and a house-hold-cleaning product. However, since 2005, Ajax also stands for Asynchronous JavaScript + XML. The technology is far from new (the underlying technology, XML HTTP requests from JavaScript, is supported by recent versions of Internet Explorer, Firefox, Safari, and Chrome—also, XML is not required at all for this), but only after this weird term was coined did people actually start using it.

The basic principle is that JavaScript can now call a remote server and then process its return values without having to reload the whole page. Of course, this has little to do with PHP; however, some Ajax classes make using Ajax from within PHP very easy.