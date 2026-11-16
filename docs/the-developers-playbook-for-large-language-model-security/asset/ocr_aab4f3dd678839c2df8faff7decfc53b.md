# User profiles

Some websites include user profiles or author bios at the end of articles or posts. Scraping such sites might accidentally gather personal details or contacts in these profiles. For example, an LLM fetching entries from a blogging platform might also scrape the author's bio, including their full name, location, workplace, and email address.

# Hidden data in web pages

Some web pages store metadata or secret information in the background. While this data may not be visible to human viewers, an LLM with web access might still access and process it. For example, an LLM scraping a corporate website might unintentionally access embedded metadata that contains internal document paths or even confidential revision comments.

# Inaccurate or broad search queries

When using search engines, if the queries are too broad or not accurately defined, the model might pull in unrelated content that contains sensitive information. For example, a query like “John Doe’s presentation” intended to find a public lecture by a notable figure might also yield results from a different John Doe’s blog where he shared his phone number for contact.

# Advertisements and sponsored content

Web scraping might inadvertently gather data from ads or sponsored posts that can sometimes contain personalized content based on prior user behavior or other targeted criteria. For example, an LLM scraping news from a web page might also pull in an ad that says “Special deals for residents of [location],” revealing location data.

# Dynamic content and pop-ups

Many websites have dynamic content that changes based on user interaction, location, or time. Pop-up surveys, chatbots, or feedback forms can contain prompts for personal information. For example, in scraping a service provider’s web page, the LLM might pull a pop-up content asking, “Are you from [city]? Answer this survey!” which can disclose geolocation details.

# Document metadata and properties

When accessing online documents or files, their associated metadata can contain author names, editing histories, or internal comments. For example, the LLM might pull a company’s public financial report, but along with it, the properties might show “last edited by [employee name] from [department],” revealing internal company information.