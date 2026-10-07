# Trust and Compliance

We will look at an example of a customer support workflow to better understand how the approval process works.

| Customer | Google Support | Google Engineer |
| --- | --- | --- |
| (Cloud Storage API) | (Support tool) | (Lower level debug tool) |
| Read object_content.pdf into Google Cloud Storage bucket /buckets/XYZ = [data corrupted] | Pull ACL on /buckets/XYZ, to handle ticket 12345 | Read/storage/customer.com/buckets/XYZ, to handle ticket 12345 |
| Let me call support to fix this. | Customer approves access | Customer approves access or bypass |
| Cloud Audit log | Access Transparency log | Access Transparency log |
| Object: /buckets/XYZ ACTION: READ | Object: /buckets/XYZ/acl Reason: Ticket #12345 | Object: /buckets/XYZ ACTION: READ Reason: Ticket #12345 |

Figure 3.2 – Access Approval workflow

In this example, the customer tries to access a file in a Google Cloud Storage bucket and is unable to access it. The customer opens a ticket. At this stage, admin activity logs are created for the API call that was made to read the object. Next, the Google support engineer, using the support tool, attempts to retrieve the access control list (ACL) for the particular bucket that the customer is trying to access. The Google support engineer does not have access, so a request is sent to the customer to either approve or deny the request. Once the customer approves the request, the Google support engineer can retrieve the ACL that was inaccessible earlier. At this stage, a transparency log entry is created that captures the object, which is bucket/XYZ/acl, the associated action, is READ, and the reason, is the ticket #12345. In the last step, the Google support engineer needs to open the file that the customer is trying to access. The reason for this is to establish that the file is now accessible, so the ticket can be resolved. Again, the support engineer will be denied access to the document and another Access Approval will be requested for the customer to take action. At this point, the customer can allow or deny the request, which depends on a number of factors, such as whether the document is sensitive. If the data inside the document is generic and not sensitive and there are no other concerns, the customer approves the request. Once the request is approved, the Google support engineer can access the document and a transparency log entry is created: OBJECT bucket/XYZ ACTION READ and REASON is the ticket number #12345.

The point of explaining the entire process of Access Approval works is to demonstrate how customers have control over their data, which is one of the Key principles we discussed in the previous section, that how Google ensures that trust is established.

You have the ability to enable Access Approval for the services you want to use it for. A list of supported Google Cloud products can be found here: https://packt.link/f5M.