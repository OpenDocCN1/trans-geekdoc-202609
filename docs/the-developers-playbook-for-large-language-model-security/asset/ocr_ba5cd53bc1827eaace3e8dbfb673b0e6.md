# Diversity

By accessing multiple top results, LLMs can gain a more comprehensive understanding of a topic from various perspectives.

# Challenges include:

# Indirect prompt injection

As discussed in Chapter 4, malicious prompts may not come directly from users. They may be secretly embedded into data included in a prompt in a RAG system. In this case, an attacker may embed malicious data within a web page, leading to an indirect prompt injection attack when the page is parsed and data is included in a prompt passed to the LLM by the application.

# Dynamic results

Search results for a particular query can change over time, introducing variability in the content the LLM accesses.

# Search limitations

Search engines may have request limits, especially for automated queries, which could restrict the number of searches.

# Depth of scraping

Deciding how many top results to scrape can affect the quality and breadth of information. Scraping too many might dilute the relevance; scraping too few might miss out on valuable perspectives.

# Legal and ethical concerns

When scraping content, it's important to abide by search engines' terms of service and consider copyright and licensing terms.

# Example risks

Direct web access or search engines carry various risks related to the unintentional acquisition or disclosure of PII and other sensitive information. Here are some examples of how this might happen:

# Comment sections and forums

A model might scrape a technical article or news piece from a reputable source, but in doing so, it could also unintentionally pull in comments or forum posts attached to the article. These sections often contain personal anecdotes, email addresses, or other identifiable details. For example, a user might ask the LLM for recent discussions on a particular health topic. The model could pull data from a health forum where users have shared personal stories, names, ages, or even specific medical details.