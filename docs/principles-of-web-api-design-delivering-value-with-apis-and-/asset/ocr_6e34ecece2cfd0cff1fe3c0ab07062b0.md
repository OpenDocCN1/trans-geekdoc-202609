API description formats provide the details of an API in machine-readable format. Tools may convert the description into human-readable documentation, generate client-side libraries, and produce a skeleton of server-side code with common patterns and practices already established.

Some API description formats support adding vendor-specific extensions. These may be used to further define authorization, routing, and configuration rules for using in automated deployments and API management layer configuration. API styles as GraphQL and gRPC provide their own respective formats. For REST-based or remote procedure (RPC)-based APIs that are built directly on top of HTTP, a separate description format is needed. This section provides an overview of popular formats to help teams select the format or formats that teams would like to use to drive their API description and documentation efforts.

Documentation examples are available in the API workshop examples' repository on GitHub.

# OpenAPI Specification

Formerly as Swagger, the OpenAPI Specification (OAS) is currently one of the most popular formats for describing the details for an API. It is managed by the Linux Foundation under the stewardship of the OpenAPI Initiative (OAI). The Swagger brand is now owned by SmartBear, which continues to maintain and support various open-source API projects under the Swagger name.

OAS came into popularity owing to the try-itout feature that is built into the Swagger UI. This project was designed to generate HTML-based API reference documentation for developers. The try-out feature allows developers and nondevelopers to explore an API against a live server from the generated documentation. It supports JSON and YAML-based formats.

OAS is currently in version 3 of the specification, although OAS v2 is still encountered in some organizations and open-source projects. The tools ecosystem is vast and continues to grow, making this a popular choice for teams building their first or thirty-first API. An example of OAS v3 is provided in Listing 13.1, based on the API design for the Shopping Cart API created in Chapter 7, “REST-Based API Design."

# Listing 13.1 Example of OpenAPI Specification v3

```
openapi: 3.0.0
info:
title: Bookstore Shopping Example
description: The Bookstore Example REST-based API supports the shopping
```

+   1. https://bit.ly/align-define-design-examples