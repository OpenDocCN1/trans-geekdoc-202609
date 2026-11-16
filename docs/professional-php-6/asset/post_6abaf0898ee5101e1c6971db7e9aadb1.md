
Each category can also be assigned its own layout, with Joomla! giving you control over various parameters (such as category order in menus, page titles, and more), as well as look and feel.

Last but not least, Joomla! supports the addition of various modules, each of which usually focuses on a specific task. For example, there are modules that show breadcrumb links, others that show archived content or custom menus, and still others that syndicate content and show polls.

Figure 22-6 shows the Joomla! Control Panel.

![](img/a1b732997d9cb194dceec0570dc79710_582_0.png)

Figure 22-6: The Joomla! Control Panel

## ExpressionEngine

ExpressionEngine is the CMS created and marketed by the folks at Ellis Lab, the same group that brought CodeIgniter (a PHP MVC framework) to the market. Of all the major CMSs out there, ExpressionEngine is the most Web 2.0-like, offering many cutting-edge features and an enormous amount of functionality for the price (around $99 for the personal license, $250 or so for the commercial license, but the core system is free to developers). Figure 22-7 shows a Web site featuring ExpressionEngine.

![](img/a1b732997d9cb194dceec0570dc79710_583_0.png)

Figure 22-7: ExpressionEngine allows for beautiful Web sites

Within the ExpressionEngine Control Panel (see Figure 22-8), you can manage CMS users, content, and templates. Creating templates (see Figure 22-9) provides you with some fairly granular control over look and feel. Each template can contain XHTML markup and expressions that are parsed by ExpressionEngine (hence, the name of the product).

## Part IV: Pushing PHP to Its Limits

![](img/a1b732997d9cb194dceec0570dc79710_584_0.png)

Figure 22-8: Adding content in ExpressionEngine

![](img/a1b732997d9cb194dceec0570dc79710_584_1.png)

Figure 22-9: ExpressionEngine templates

These expressions can be as simple as adding a custom bit of text, or looping through blog posts in a sidebar. For example, if you were to publish a list of books on your site, you could create custom fields such as Author, ISBN, Title, Publish Year, and Language, all of which can be used by ExpressionEngine in other parts of your site. For example, you could list all books by a certain author, or published in a certain year. You could also designate a certain custom field as a drop-down list or date field, for example.

Furthermore, the way that templates work with the rest of your site is ingeniously simple. You can group your templates in such a way that you create self-explanatory URL paths. For example, you can create a template group called “Services” and place your services-related pages in that template.

## Frog CMS

Frog CMS was born as phpRadiant, a PHP version of the popular Rails-based Radiant CMS. Its tagline is “Content Management Simplified” (see Figure 22-10), and anyone who uses it would have to agree. It offers a very elegant user interface, a flexible templating engine, and the bare-bones tools needed for user and asset (file) management (see Figure 22-11).

![](img/a1b732997d9cb194dceec0570dc79710_585_0.png)

Figure 22-10: Home page of the Frog CMS site

![](img/a1b732997d9cb194dceec0570dc79710_586_0.png)

Figure 22-11: Managing pages in Frog CMS

Users can create snippets for their layouts (see Figure 22-12), each of which is a reusable piece of code such as a header or a footer. Snippets can also be pure content, such as a list of links or a graphic. Frog CMS also enables users to create content using a simplified HTML editor.

![](img/a1b732997d9cb194dceec0570dc79710_587_0.png)

Figure 22-12: Managing snippets in Frog CMS

Last, but not least, you can add modules (usually plug-ins or themes) to Frog CMS, thereby extending it. Core plug-ins include archival features, comments, file management, 404 custom page controls, and SQLite. Already, the user community has created an entire library of plug-ins, including polls, download management, newsletters, contact forms, and more.

## Building Your Own System

One of the interesting things about the world of content management is that many organizations have what may be called “unique local requirements” — in other words, they have such one-off needs regarding the creation, publication, management, and syndication of content that no off-the-shelf program (whether free or commercial) is appropriate. Nor will it do to modify any off-the-shelf system.

Instead, a vast percentage of content management projects involve some healthy amount of do-it-yourself programming. If you’re participating in one of these ventures, here’s a roundup of requirements that will make the short list on any project. Included in this roundup are some technical details to help you clarify your thought process. It’s not comprehensive, but it’s a good start.

### Content-Related Issues

It always seems to be a shocking revelation to some developers, but the whole point of a content management system is to *manage content*. This point is brought up only because most projects seem to devolve into strange quagmires involving workflow engines and database caching.

Content is king. Everything else is subservient to that statement. The beating heart of content is the *content type* — which is just elementary shorthand for how content is structured and used. Most people intuitively understand that a press release is somehow different from a blog post. They not only have different component parts, but different uses and different audiences.

To that end, you could push out a CMS that has a fixed set of content types:

- [ ] Web page
- [ ] Article
- [ ] Blog post
- [ ] Press release
- [ ] News feed

Each of these may have its own particular set of data fields (such as title, byline, summary, publication date, and so on). Alternatively, you could push out a system that allows users to define their own content types.

If you pick the former, which always appears to be the easier undertaking (after all, creating a dynamic content construction system is a lot of work), then you must be prepared to live with the constant need to create new content types and alter those that seemed like a good idea during development but have now met the harsh sunlight of after-launch expectations, and have started to fade.

If you pick the latter, and allow administrators to define their own content types, then you must ask yourself how you define a content type. The answer to that question isn’t altogether obvious until you’ve thought about it for a while, and no single answer is 100 percent correct. However, one bit of advice has always led to good outcomes; define a content type as the confluence of two sets of criteria:

- [ ] What metadata is associated with the content type? (This would be the nouns and adjectives.)
- [ ] What behaviors are associated with the content type? (This would be the verbs and adverbs.)

Once you have this mental framework in place, the noun/verb metaphor becomes a handy way to express any content type.

Let’s take a press release as a starting point. If you think about a press release’s morphology (that’s fancy talk for “the parts of it”), you can easily translate those parts into metadata. Each press release has the following components (as a rough start):

- [ ] Headline
- [ ] Subhead
- [ ] Date slug
- [ ] Summary
- [ ] Body
- [ ] Contact information
- [ ] Keywords/tags/categories

Given enough time, you could discover a whole other group of metadata that may or may not be needed by your organization's PR group. Suffice it to say, you have enough to get started.

Stopping the discovery at nouns, however, would give you an incomplete view of what a press release is. Most organizations also need press releases to function in a certain way — in other words, a press release also has behaviors associated with it. For example, each press release also has a launch window, usually expressed as a date and time (often after the market closes). It also includes legal language bits that make the regulatory folks happy (if they are present) or unhappy (if they are not).

These “verby” parts of a press release are also embodied as metadata; but the main difference is that the system must be aware of them and do something in response to what is stored there. For example, the legal bits had better be present in order for the press release to be launched. A smart CMS shouldn’t allow a press release to go live without alerting someone that the legal bits are missing or incorrect. The same thing applies to the launch window — if the press release is categorized in a certain way (for example, its contents are tagged as financial or market news), then the CMS shouldn’t allow posting before market close.

Once you’ve mapped out what’s needed for press releases, do the same for all the other possible content types that the client needs now (and may need later). You’ll inevitably find a lot of similarities in both nouns and verbs across all your content types. In fact, you’ll note that just about every piece has a headline, a date, an author, keywords, content body, and so on. Some content types will have special needs (such as events, which might also have a signup URL and a reminder widget). For that reason, you should consider nonglobal metadata that can be added to individual types.

Once you have your technical design down for content, you must decide which path you’ll take. If you give your client hard-coded content types, then you’ll probably end up with different database tables for each content type. If that’s the case, make it very easy to add new content types in the future. Here’s where a good MVC design comes in, which gives you the capability to easily add a database table for, say, calendar events, along with its model, admin controllers, and any views for CRUD (create, review, update, and delete).

If you go the other route, then you’ll probably end up with a centralized table that houses all of your interchangeable blocks of content (a headline block, a byline block, a date block, a content body, and so on), and then give users the capability to reuse, rename, and connect those blocks — in any way they choose — into bigger blocks that are called *content types*.

Don’t forget, though, that either way, you must devise some way to tell the CMS what’s important about your metadata. In other words, if you hard-code the content types, you must have a way to tell the CMS that no article can be posted without a headline, or a press release must follow certain workflow rules. The same is true if you give administrators the freedom to devise their own content types.
