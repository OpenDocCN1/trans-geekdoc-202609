# Web Services

Web scraping applications are often built because the target application offers no web service or data formatted for automated consumption. However, some of these sites do eventually come to offer a web service after the web scraping application has already been built. As such, it's important to keep this potential eventuality in mind during the design phase.

The introduction of a web service will not negate previously described concerns regarding retrieval. Latency can still prove to be an issue for an application that attempts to access either the target application or a corresponding web service in real-time. Ideally, complexity will be reduced and performance increased in the analysis process when switching from a web scraping application to an API.

However, both areas of code will likely need to be replaced if an API offering does materialize. As such, it's important to design an API that approximates a hypothetical web service offering as closely as possible and centralizes logic that will need to be replaced in that event. By doing so, existing local application logic that uses the existing API will require little or no change.

Legalities aside (see Appendix A for more on those), there are reasons to consider maintaining an existing web scraping application over a new web service offering. These can include web service data offerings being limited or incomplete by comparison or uptime of the web service being below an acceptable tolerance. In the former case, web scraping logic can be replaced with web service calls where the two data offerings overlap for increased data reliability. In the latter case, the web scraping logic can conduct web service calls when the service is available and use cached data or store data updates locally until the service becomes available again.

# Testing

As important as unit testing is to quality assurance for an application, it's all the more important to a web scraping application because it's reliant on its target to remain unchanged. Queries of markup documents must be checked to assert that they produce predictable results and data extracted from those markup documents must be validated to ensure that it is consistent with expectations. In the case of real-time applications, HTTP responses must also be checked to ensure that the target appli-