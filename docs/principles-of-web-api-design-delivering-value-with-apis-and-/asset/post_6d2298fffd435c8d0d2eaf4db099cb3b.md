
# THE MINIMUM VIABLE PORTAL 257

| Section | Questions to Answer | Information to Include |
| :--- | :--- | :--- |
| Workflows | What is the optimal/assumed workflow for the two or three most useful things users can do with your API? | Link to the reference for each operation mentioned in the workflow |
| Code samples | What does the code look like for a "hello world" and common use cases? | Complete code samples and code snippets that users can copy and paste For each operation: HTTP method (GET, PUT, POST, DELETE) |
| Reference | What do users need to know to use each operation? | Complete request URL Parameters (path and query): name, type, description, and whether the parameter is required; Example request (including header and body); List of each element in the example request, including the type, description, and whether the element is required; Example response; List of each element in the example response, including type and description; List of error and status codes, including the code, message, and meaning |

Once all items on this list are checked off for all sections, the API developer portal is in good shape to support the needs of initial consumers involved in the early stages of API design as the needs of future consumers who may discover the API. Depending on available expertise and the number of API operations, the effort required to complete this phase may take between one and three weeks. If necessary, focus on the most common use cases that the API addresses, incorporate additional documentation in future phases.

# Phase 2: Improvement

The best place to spend time improving the portal will depend on the characteristics of the API. If the API has changed, new operations, or works differently than previously documented, the first priority is updating the docs to incorporate the changes. But if everything is up to date, consider some of the ideas in Table 13.2 as time allows.

# Table 13.2 Improving the Developer Portal

| Type of Improvement | Recommended Improvements |
| :--- | :--- |
| Quick (one or two days) | Add a changelog to list API enhancements and fixes<br>Standardize terminology—make sure you use the same terms to mean the same thing throughout the docs<br>Tweak use cases and examples to make sure they’re oriented<br>Add chat-based support or public discussion forum for the API<br>Add a page that links to users' projects and blog posts about your API (e.g., Sunlight Foundation lists projects that need help and projects that are ready to use)<br>Create a shared product roadmap |
| Not-so-quick (three or more days) | Revise all content with a user-centric rather than developer-centric focus<br>Update text to include terms users are likely to search for<br>Review the references for missing, incomplete, or confusing information<br>Reorganize to improve logical order of sections and content<br>Add business-focused content for nontechnical users and decision makers<br>Implement a new publishing tool<br>Extend code examples into complete tutorials<br>Create reference apps, available via GitHub, to help developers get started quickly |

# Phase 3: Focusing on Growth

Once the items from the first two phases that are relevant to the team have been completed, consider a few additional improvements to shift the portal from supporting customers to generating growth in adoption:

- **Add case studies**: Case studies demonstrate an API’s value by describing how clients have used it to solve a problem, expand business, or succeed in some way. Add depth and meaning to API documentation by offering real-world context, which helps readers understand how the API has already benefited others and could benefit them too. Case studies can even inspire some new ideas for using an API. If “Case Studies” sounds a little dry or academic, try something like “Success Stories” or “Client Stories” instead.

- **Adding started guides**: Readers who understand how APIs work might be able to start using an API with authentication alone, but what about users who are less comfortable? A getting started guide should build users' confidence that they can use the API and inspire them to dig deeper into the rest of the documentation.

- **Incorporate analytics**: Analytics help portal administrators tailor the portal to the needs of the audience based on real data about traffic patterns and help readers move more smoothly through the content.

- **Move to single-page format**: Consider restructuring some portions of the portal on a single page. The benefit of this format is that users navigate the documentation either with the menu that links to all the section headers or by Ctrl/Cmd+F to search for text on the page.

- **Translate the documentation**: As the API gains traction, consider whether documentation translation would be helpful. Professional translation is expensive and takes time; a clear and persuasive business case is necessary before starting this journey. It's rare, but some teams discover that most of their users are in another country and therefore would benefit from translated documentation.

Finally, continually check around to see what other companies with successful APIs are doing with their documentation. Then produce a plan for incorporating these new ideas into the developer portal to benefit customers, partners, and internal developers.

# Tools and Frameworks for Developer Portals

One of the challenges of establishing a developer portal is to select a tool, or a series of tools, that helps produce the developer portal. Outlined here are tools that organizations have used to produce their developer portal:

- **Static site generators**: Tools such as Jekyll, used to power GitHub pages, and Hugo are popular choices for creating and managing developer portals. Pages are authored using Markdown or similar notation and are stored in a code repository. Deployment is typically automated to ensure the latest version of the documentation is published once changes are merged into the main branch.

- **SwaggerUI**: This is the tool that started it all for the Swagger description format, now separated from the tool as the OAS. This open-source codebase renders any OAS v2 or v3 specification, plus older Swagger specification files, into API reference documents in HTML format.

- **MVP template**: I have collaborated with others to create a GitHub project for starting an API developer MVP that is based in Jekyll. It helps to combine the static generator with some placeholders for content and integrating Swagger or similar reference documents into a single location. Fork the repository at https://github.com/launchy/mvp-template and customize as needed to get started quickly.

Whatever tools are selected, be sure to provide any machine-readable descriptions, such as OAS files, as part of the portal. This will allow developers to apply their own tooling, as custom code generators, for speeding up the integration process.

Finally, be sure to research open-source and commercial tools that can assist in the creation and management of the developer portal. Some API management (APIM) layers, detailed in Chapter 15, offer portal management support as well.

# Summary

Establishing an API documentation strategy is part of delivering a successful API product, formalized API program, or enterprise API platform. Developer portals must support a variety of personas. It is critical to ensure that documentation is part of the overall API design and delivery lifecycle. Otherwise, it becomes a last-minute task that results in poor documentation that fails to meet the needs of the target personas.

Seek to include documentation and API portal updates as part of the overall delivery schedule. An API should be considered only when the documentation is updated alongside the release. This approach to documentation will produce a more complete API that encourages rapid adoption by developers and other decision makers.
