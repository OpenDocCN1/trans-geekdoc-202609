# Chapter 5: Cloud Application Security

The 2.0 standard was adopted in 2005 and provides a standard framework for the XML assertions and standardized naming conventions for its elements. In a federated system, when an entity authenticates through an identity provider, it sends a SAML assertion to the service provider containing all the information the service provider requires to determine the identity, level of access granted, or any other information or attributes about the entity.

# OAuth

OAuth was established originally in 2006 and is published in RFC 6749, found at http://tools.ietf.org/html/rfc6749. The following is from the official RFC abstract:

The OAuth 2.0 authorization framework enables a third-party application to obtain limited access to an HTTP service, either on behalf of a resource owner by orchestrating an approval interaction between the resource owner and the HTTP service, or by allowing the third-party application to obtain access on its own behalf.

# OpenID

OpenID is an authentication protocol based on OAuth 2.0 specifications. It is designed to provide developers with an easy and flexible mechanism to support authentication across organizations and utilize external identity providers, alleviating the need to maintain their own password stores and systems. Developers can leverage OpenID as an open and free authentication mechanism and tie it into their code and applications, without being dependent on a proprietary or inflexible system. With a browser tie-in for authentication, OpenID provides web-based applications an authentication mechanism that is not dependent on the particular clients or devices used to access it. Information about OpenID and official specifications can be found at the OpenID website, http://openid.net.

# WS-Federation

WS-Federation is an extension to the WS-Security standards, also published by OASIS. The following is from the official abstract of the WS-Federation 1.2 Specification, found at http://docs.oasis-open.org/wsfed/federation/v1.2/os/ws-federation-1.2-spec-os.html:

This specification defines mechanisms to allow secure realms to federate, that authorized access to resources managed in one realm can be provided to security principals whose identities and attributes are managed in other realms. This includes mechanisms for brokering of identity, attribute, authentication and authorization assertions between realms, and privacy of federated clients.

By using the XML, SOAP, and WSDL extensibility models, the WS-* specifications are designed to be composed with each other to provide a rich Web environment. WS-Federation by itself does not provide a complete security solution for Web services. WS-Federation is a building block that is used in conjunction with other Web service, transport, and application-specific protocols to accommodate a wide variety of security models.

181