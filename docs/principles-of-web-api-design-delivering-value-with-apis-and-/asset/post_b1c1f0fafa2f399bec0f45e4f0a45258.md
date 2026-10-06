
- Authentication and authorization: This element describes how to obtain an API token with the appropriate authorization scopes necessary to use the API as desired.

- API reference documentation: Details on each operation, including URL path structures, input and output data structures, and error data structures, are given in the reference documentation.

- Release notes and changelog: The changes in each release, including new operations and enhancements to existing operations, are summarized in a historical format.

Beyond these essential elements, developer portals seek to inform and deliver on the following experiences:

- Easy onboarding: APIs rarely gain adoption if it is difficult to get started. Easy onboarding, from self-registration to a guided tour and API token creation, helps developers overcome the challenges of adopting a new API. Integration between the developer portal and the API gateway is responsible for provisioning API tokens is important to effective onboarding.

- Operational insight: Is the API available or temporarily down? A simple status page that reflects an API's availability helps to inform developers and operations staff who saw increased errors in their applications.

- Live support: Including a chat solution, whether embedded into the developer portal or through a communication platform such as Slack, WebEx, or Microsoft Teams, provides direct access to those who can resolve integration. The team responsible for live support is often called developer relations, or DevRel for short. They might be responsible for the developer portal alongside developer support.

## Effective API Documentation

To write clear documentation, it is important to answer the questions commonly asked by those considering the adoption of an API. The answers to these questions may be obtained through interviews conducted with developers integrating the API.

It is important to engage in conversations with them whenever possible. Engaging in discussions with API consumers will lead to those critical “aha!” moments API providers need to improve their documentation.

# CHAPTER 13 DOCUMENT THE API DESIGN

When discussion with API consumers is not possible, try to find other developers to review the documentation. Conduct a documentation audit by defining a mythical scenario, writing some code to call the API to produce a prototype. Along the way, ask questions to identify areas of improvement for the API documentation offered.

## Question 1: How Does Your API Solve My Problems?

Ensure that the API documentation has an introduction that covers what the API solves and what it doesn't solve and it offers example cases that the API has solved in the past. This information establishes a context for the reader, who may be deciding whether the API is the right fit for their need.

## Question 2: What Problem Does Each API Operation Support?

Add documentation to clarify what each operation does and when it is applicable. "Get all accounts" is not a helpful description of an API operation. Add details about what kinds of filters, implied or explicit, are supported.

Offer some example scenarios describing how an API operation may be used or how it may be combined with other operations to achieve particular outcomes. The job stories and API profiles created during the Align-Define-Design-Refine (ADDR) process is a good source for this detail.

## Question 3: How do I Get Started Using the API?

If the API offers self-service onboarding, call out this in the documentation as a benefit to getting started faster. For those who require time to go through a partnership program, include details of the program in the documentation as well. This information ensures that the appropriate time is factored in prior to developers beginning the first hello world integration.

It is important to offer links to the onboarding process in various locations of the API documentation. Not all developers start from the homepage of the developer portal. Publicly accessible reference documentation will be indexed by search engines, creating organic points into a developer portal. Be to include a link to the onboarding process somewhere near the top of the reference API documentation.

Finally, don't assume that all developers can figure out how to use an API. Every developer is at a different stage in their career. Some may have the more, or less experience than others using Web APIs. Take the time to explain, step by step, how to get started.

## The Role of Technical Writer in API Docs

Traditionally, technical writers focused on delivering manuals for software, often in PDF or HTML format. These manuals consisted of screenshots and step-by-step guidance for using software. Extensive knowledge of the user interface, including features that are often overlooked, was required. The role was crucial for ensuring end users were able to use the software effectively and efficiently while reducing support costs. Rarely, technical writers were required to have a deep knowledge of one or more programming languages, such as C/C++, Java, or Python.

Over the past decade, the role of technical writers has undergone a transition. In some organizations, technical writers have been replaced by user experience (UX) experts who design user interfaces that require minimal or no documentation. Other organizations replaced technical writers with marketing and product roles that improve the copy of an app to increase conversion or increased usage metrics.

With growth of APIs, technical writers are again in heavy demand. They are required to understand how to use APIs directly via HTTP, with a variety of programming languages to demonstrate API integration using Java, Python, GoLang, Ruby, JavaScript, Objective-C, Swift, command-line automation, and more. Their target audience spans ends, experienced developers, and developers right out of college. Rather than documentation efforts focused on a few large releases per year, now releases may occur on a weekly or daily basis owing to deployment and cloud infrastructure.

The value that technical writers offer to any product is enormous. For APIs, their talent is invaluable. They provide an outside-in perspective on an API’s design and documentation to ensure it provides value to the target audience. Questions around the purpose and intended use of each API operation help to hone the API design early.

The challenge for most technical writers is building a sufficient team to handle the vast amount of work before, during, and after every release of API offered by the organization. A single technical writer for a small API may be able to keep documentation updated. If the organization is large and offers multiple APIs, the challenge increases beyond the capabilities of even the most talented technical writer. Therefore, it is critical that organizations have a team of technical writers. This team should be able to dedicate a few technical writers for emerging APIs while others are focused on maintaining documentation for existing APIs. All decisions regarding API documentation tools and process should be made by the technical writers, not by developers forcing specific tools upon them. They should be considered first-class team members rather than a siloed team that has API implementations thrown at them at the last minute for a quick-and-dirty documentation effort.

Finally, remember that API documentation is the user interface for developers. Technical writers can make or break an API's success. The same can be said for enterprise API platforms where some APIs are targeting partners, customers, and third-party service integrators.

## Minimum Viable Portal

The minimum viable portal (MVP) builds on the idea of the minimum viable product from lean processes to establish a phased approach to delivering a developer portal. The MVP provides prioritization as three phases, the first being the minimal developer portal needs. As the team matures the API, the developer portal may be enhanced by taking it from minimum documentation to a robust developer portal.

## Phase 1: Minimum Viable Portal

The checklist in Table 13.1 lists the five most important modules to provide in an initial API developer portal. Included in the table are questions to answer and information to include in each section to help the process.

| Table 13.1 Minimum Viable Portal Checklist |
| Section | Questions to Answer | Information to Include |
|---|---|---|
| Overview | What type of API do you have? | Type of API (RESTful, SOAP, gRPC, GraphQL, etc.) |
| | What can users do with your API? | Brief use cases and examples (two or three sentences) |
| | Are there any access details or restrictions users need to know? | Base URL, rate limits |
| Authentication | If your API requires an authentication token or key, how do users get one? | Authentication method |
| | Do tokens/keys expire? | Expiration intervals (if any) |
| | What should users do if their token/key expires? | Refreshing expired tokens/keys |
| | How do users pass authentication to your API? | Example authorization header |
