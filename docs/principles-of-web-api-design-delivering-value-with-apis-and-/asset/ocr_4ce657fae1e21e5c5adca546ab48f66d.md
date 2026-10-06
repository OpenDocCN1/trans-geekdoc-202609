# CHAPTER 14 DESIGNING FOR CHANGE

The fictional online bookstore example used throughout this book assumes that the APIs identified throughout the process did not already exist, resulting in a greenfield project. The reality is that organizations already have APIs in production for a variety of purposes, and any proposed API designs must fit the reality that brownfield development will be required.

These brownfield initiatives are forced to reconcile the findings from the ADDR process with any existing API designs to determine the best path forward. This chapter details some considerations for handling change when APIs already exist.

# Perform an API Design Gap Analysis

Teams should perform a gap assessment of the ideal API design identified during the process with the way it is designed today. The team must then determine whether to follow the same style and design decisions of the API design for consistency, mix the new design alongside the older design decisions, or consider alternatives.

Factors to consider when performing this design gap analysis include the:

+   - Introduction of differing terminology for resources and resource properties during the design process
- A shift from data-centric to resource-centric API design styles
- Change in vision and direction for the API product compared to what exists today

Using these factors as a starting point, itemize the differences between existing APIs and the ideal API design created as a result of the ADDR process. Assign a sizing for the value provided to API consumers by the new design and the size of the impact in API design change. Using t-shirt sizing (e.g., small, medium, large, extra-large) ensures the measurement is an effective way to size the value and impact. Then determine what is best for API consumers.

# Determine What Is Best for API Consumers

Making an API design decision, particularly when breaking changes will be required, involves more than the direct impact to the organization. It must also include what is best for API consumers.