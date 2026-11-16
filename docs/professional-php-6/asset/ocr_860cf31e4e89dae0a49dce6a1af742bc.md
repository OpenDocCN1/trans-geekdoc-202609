# # Content-Related Issues

It always seems to be a shocking revelation to some developers, but the whole point of a content management system is to *manage content*. This point is brought up only because most projects seem to devolve into strange quagmires involving workflow engines and database caching.

Content is king. Everything else is subservient to that statement. The beating heart of content is the *content type* — which is just elementary shorthand for how content is structured and used. Most people intuitively understand that a press release is somehow different from a blog post. They not only have different component parts, but different uses and different audiences.

To that end, you could push out a CMS that has a fixed set of content types:

+   - [ ] Web page
+   - [ ] Article
+   - [ ] Blog post
+   - [ ] Press release
+   - [ ] News feed

Each of these may have its own particular set of data fields (such as title, byline, summary, publication date, and so on). Alternatively, you could push out a system that allows users to define their own content types.

If you pick the former, which always appears to be the easier undertaking (after all, creating a dynamic content construction system is a lot of work), then you must be prepared to live with the constant need to create new content types and alter those that seemed like a good idea during development but have now met the harsh sunlight of after-launch expectations, and have started to fade.

If you pick the latter, and allow administrators to define their own content types, then you must ask yourself how you define a content type. The answer to that question isn’t altogether obvious until you’ve thought about it for a while, and no single answer is 100 percent correct. However, one bit of advice has always led to good outcomes; define a content type as the confluence of two sets of criteria:

+   - [ ] What metadata is associated with the content type? (This would be the nouns and adjectives.)
+   - [ ] What behaviors are associated with the content type? (This would be the verbs and adverbs.)

Once you have this mental framework in place, the noun/verb metaphor becomes a handy way to express any content type.

Let’s take a press release as a starting point. If you think about a press release’s morphology (that’s fancy talk for “the parts of it”), you can easily translate those parts into metadata. Each press release has the following components (as a rough start):

+   - [ ] Headline
+   - [ ] Subhead
+   - [ ] Date slug