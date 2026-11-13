Here is a sample request sent to Amazon, as shown in Figure 12.4, to return information about possible book matches for a keyword or series of keywords.

```
http://ecs.amazonaws.com/onca/xml?Service=AWSECommerceService&AWSAccessKeyId={AWS_ACCESS_KEY}&Operation=ItemSearch&SearchIndex=Books&ResponseGroup=Medium&Keywords={SEARCH_TERMS}
```

The AWS_ACCESS_KEY is the access id that is provided by Amazon, and the SEARCH_TERMS would be the keyword(s) that are passed along for searching.

As you may have noticed, the XML response from Amazon is fairly complex. However, for this example the focus will be on the book title, author, and thumbnail path. Amazon is actually very nice to provide the amount of detail it does. You can build some pretty interesting applications with the AWS system.

# FIGURE 12.4

Here is the XML response from Amazon, after a search for “PHP”.

![](bbox=[0.1, 0.43, 0.74, 0.82])