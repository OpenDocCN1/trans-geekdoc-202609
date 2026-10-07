# Identity-Aware Proxy

We will use the illustration given in Figure 8.8 to understand the flow and the key components of IAP
for-premises. We will then look at how secure access is given to applications that are connected
ia a hybrid connector from Google Cloud to on-premises.

The initial part of the workflow is similar to how IAP works for App Engine, as explained earlier. There
is no difference between the authentication and authorization checks that are performed for the user.
The request is then sent to the IAP connector, which forwards the request to the on-premises network
over a site-to-site connection by Interconnect.

IAP targets on-premises applications with the use of an IAP connector. You can create an IAP
connector from the IAM dashboard of the Google Cloud console. An IAP connector is deployed using
a configurable Google Cloud Deployment manager. This template deploys the resources that
need host and run the IAP connector. Inside your Google Cloud project, the template deploys
An Ambassador proxy on a GKE cluster. This proxy is responsible for routing the traffic that is secured
by Cloud Identity to your on-premises applications, directly applying Google Cloud Identity and
Access Management (Cloud IAM) policies.

You have to define the mappings for the IAP connector. Every routing name must correspond
an an ambassador-created GCE backend resource. The mapping parameter has to define the routing
with the source and destination. This is to ensure that the requests can be routed from the source
to the correct destination, which could be an application on the on-premises network. The following
example shows what a mapping should look like:

```
routing:
  - name: crm
    mapping:
      name: host
      source: www.crm-domain.com
      destination: crm-internal.domain.com
  - name: sub
      source: customer.hr-domain.com
      destination: customer.hr-internal.domain.com
  - name: billing
    mapping:
      name: host
      source: www.billing-domain.com
      destination: billing-internal.domain.com
```

In this example, we route the incoming requests coming from www.crm-domain.com to
crm-internal.domain.com and therefore create a mapping for both the host and subdomain
as well. Later, we will look at the steps to enable IAP for on-premises applications.