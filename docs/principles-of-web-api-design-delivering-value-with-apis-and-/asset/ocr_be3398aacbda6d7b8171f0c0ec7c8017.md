# What about Using the OpenAPI Specification?

The OpenAPI Specification (OAS) is a machine-readable format used to capture the description of REST-based and gRPC-based APIs. The format was designed to aid in the generation of API reference documentation and boilerplate code. As such, the OAS structure is rooted in URL paths. Because API modeling precedes a complete API design that includes resource paths, OAS isn't an appropriate format for API profiles. However, API profiles will help accelerate the creation of OAS-based API descriptions later in the design process.

API teams have found that using the Application-Level Semantics (ALPS) specification, detailed in Chapter 13, “Document the API Design,” is a useful way to produce a machine-readable API profile that may be used to accelerate the API modeling and design process independent of the chosen style(s).

The specifics about using the OAS to capture the API description of a REST-based API design is addressed in Chapter 7, “REST-Based API Design.”

Those who have the artifacts from the previous Align-Define-Design-Refine (ADDR) steps will typically complete the API modeling process in two hours. For those who skipped some of the steps, API modeling may take several hours to complete.

# Step 1: Capture API Profile Summary

The first step is to fill out the basic details of the API profile, including the API name, a short description, and the scope of the API. The scope of the API should correspond to the scopes that the organization supports, internal, public, and partner. Remember that these details can be changed as the team gains more understanding about the process and responsibilities of each API.

Next, capture the API operation names and participants based on the activities and activity steps captured previously. For each activity step identified previously, convert it into an operation name that uses a consistent naming format. It is suggested to use lowerCamelCase, which makes it easier for the team to explore the API model using sequence diagrams, as recommended later in this chapter.

Figure 6.3 demonstrates how to capture the start of an API profile using JSON’s Bookstore’s Shopping API, previously identified during the Align phase of the design process.