# # Chapter 3

# ## HTTP Streams Wrapper

At this point, you should be fairly well-acquainted with some of the general concepts involved in using an HTTP client. The next few chapters will review some of the more popular mainstream client libraries, particularly common use cases and the advantages and disadvantages of each. This client covered in this chapter will be the HTTP streams wrapper.

PHP 4.3 saw the addition of the Streams extension to the core. According to the related section of the PHP manual, the intention was to provide “a way of general- izing file, network, data compression, and other operations which share a common set of functions and uses.” Streams introduced several concepts, one of which is a **wrapper**. The job of a wrapper is to define how a stream handles communications in a specific protocol or using a specific encoding. One such protocol for which a wrapper is available is HTTP

The advantage to the HTTP streams wrapper is that there is very little to learn in terms of the API. It’s fairly easy to get something simple working quickly. The disad- vantage is that it’s very minimalistic in terms of the feature set offered. It gives you the ability to send HTTP requests without having to construct them entirely on your own (by specifying the body and optionally any headers you want to add) and access data in the response. That’s about it. The ability to debug requests is one example of a feature that it does not include at the time of writing.

The fact that the wrapper is written in C is a bit of a double-edged sword. On the positive side, there is a substantial performance difference between C code and PHP