+   - Retrieval of information from directory/data repository infrastructure
+   - Revocation status verification
+   - Construction and processing of trust chains

Additional information about the signer’s public signing key ("< ds:KeyInfo >") can be included inside the signature block, which can be used to help the verifier determine which public key certificate to select.

Information contained in the < ds:KeyInfo > element may or may not be cryptographically bound to the signature itself. Therefore, < ds:KeyInfo> element data can be replaced or extended without invalidating the digital signature. For example, Valerie signs a document and sends it to Jim with a <ds:KeyInfo > element that specifies only the signing key data. On receiving the message, Jim retrieves additional information required to validate the signature and adds this information into the < ds:KeyInfo > element when he passes the document on to Yolanda (see Figure 3.40).

![](bbox=[0.08, 0.47, 0.92, 0.87])

Figure 3.40 - The XKMS service shields the client application from the complexities of the underlying PKI.

The X-KISS Locate service resolves a < ds:Keyinfo > element but does not require the service to make an assertion concerning the validity of the binding between the data in