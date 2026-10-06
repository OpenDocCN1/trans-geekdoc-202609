# 206 CHAPTER 10 FROM APIs TO MICROSERVICES

![](bbox=[0.125, 0.114, 0.792, 0.638])

**Figure 10.10** The search engine integration will require specialized knowledge of how to properly index and search entities, so the Search Books operation is a good candidate for a separate microservice.

ensuring the search engine indexes are both performant and deliver the capabilities required by customers. Figure 10.10 show the boundary for the candidate microservice that will support book searches.

# Step 2: Add Microservices into API Sequence Diagrams

Next, revise the sequence diagram to show the introduction of the candidate microservice. Determine if the integration should use a synchronous API, such as REST, or if an asynchronous service would be better. An updated sequence diagram for the Shopping API is shown in Figure 10.11.