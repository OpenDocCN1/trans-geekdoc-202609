# Cloud Data Loss Prevention

+   - Ideally, do not include on-premises corp networks with user devices within a very secure service perimeter configuration.
- Document the following for every use case you use VPC Service Controls for:
  - The access pattern
  - The actors that can trigger the use case
  - Conditions that trigger the use case
  - Whether the use case is a valid access pattern and should be allowed
  - Any assumptions that pertain to the use case
- Treat VPC Service Controls logically the same way you would a firewall; in the network, you need to "know your flows"' to successfully secure the environment with the required ingress and egress flows enabled

VPC Service Controls is an important part of your cloud security strategy, so make sure you spend enough time understanding it.

# Summary

We have covered a lot of things in this chapter. We went over various DLP definitions, use cases, and architecture options. We went over in detail how to use DLP for inspection and de-identification. We also saw examples of how to call DLP APIs and how to interpret the response. Last but not least, we went over data exiltration strategies such as VPC Service Controls and their best practices. In the next chapter, we will go over the features of Secret Manager and how it can be used to store your application secrets.

# Further reading

For more information on Cloud DLP and VPC Service Controls, refer to the following links:

+   - InfoDetector reference: https://packt.link/cVC5r
- Access level design: https://packt.link/ZAEAk4
- Creating device-based access levels for VPC Service Controls: https://packt.link/MpHWv
- Ingress and egress rules for VPC Service Controls: https://packt.link/3bBkP