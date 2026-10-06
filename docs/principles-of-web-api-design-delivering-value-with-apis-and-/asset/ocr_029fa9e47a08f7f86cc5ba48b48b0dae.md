# CHAPTER 13 DOCUMENT THE API DESIGN

When discussion with API consumers is not possible, try to find other developers to review the documentation. Conduct a documentation audit by defining a mythical scenario, writing some code to call the API to produce a prototype. Along the way, ask questions to identify areas of improvement for the API documentation offered.

# Question 1: How Does Your API Solve My Problems?

Ensure that the API documentation has an introduction that covers what the API solves and what it doesn't solve and it offers example cases that the API has solved in the past. This information establishes a context for the reader, who may be deciding whether the API is the right fit for their need.

# Question 2: What Problem Does Each API Operation Support?

Add documentation to clarify what each operation does and when it is applicable. "Get all accounts" is not a helpful description of an API operation. Add details about what kinds of filters, implied or explicit, are supported.

Offer some example scenarios describing how an API operation may be used or how it may be combined with other operations to achieve particular outcomes. The job stories and API profiles created during the Align-Define-Design-Refine (ADDR) process is a good source for this detail.

# Question 3: How Do I Get Started Using the API?

If the API offers self-service onboarding, call out this in the documentation as a benefit to getting started faster. For those who require time to go through a partnership program, include details of the program in the documentation as well. This information ensures that the appropriate time is factored in prior to developers beginning the first hello world integration.

It is important to offer links to the onboarding process in various locations of the API documentation. Not all developers start from the homepage of the developer portal. Publicly accessible reference documentation will be indexed by search engines, creating organic points into a developer portal. Be to include a link to the onboarding process somewhere near the top of the reference API documentation.

Finally, don't assume that all developers can figure out how to use an API. Every developer is at a different stage in their career. Some may have the more, or less experience than others using Web APIs. Take the time to explain, step by step, how to get started.