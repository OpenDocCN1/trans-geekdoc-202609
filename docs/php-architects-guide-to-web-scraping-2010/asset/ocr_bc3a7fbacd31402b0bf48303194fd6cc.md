# Chapter 9

# Tidy Extension

At this point, you should have completed the retrieval phase of the web scraping process and have your raw response body ready and awaiting analysis. Congratulations on making it to the halfway mark.

While other response formats are certainly possible, chances are good that you are dealing with a markup-based language like HTML or XHTML. As such, this chapter and subsequent chapters will deal specifically with those formats. More often than not, HTML will be the language in use.

There are a number of available XML-focused PHP extensions that can deal with markup, which will be reviewed in chapters to follow. While these extensions do provide some support for HTML and are even somewhat forgiving about malformed markup, well-formed XHTML is their ideal input. This being the case, the first step in the analysis process is to perform any necessary cleanup on the response body in order to minimize the number of issues that can be encountered later during analysis.

# Validation

The World Wide Web Consortium (W3C) provides a markup validation service in order to promote adherence to web standards. You can access this service by going to `http://validator.w3.org`. It accepts markup to be tested by URL, file upload, or