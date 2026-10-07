
# Identity-Aware Proxy

![](img/f681dfc12450e3a4c257352b70dbceca_217_0.png)

Figure 8.7 – How IAP works with App Engine

Let's look at Figure 8.7 to understand how IAP works with App Engine. When an application or resource is protected by IAP, only users with the appropriate IAP rights (the IAP-secured Web App User role) can access it. In order to access protected resources, IAP runs both authentication and authorization checks on the requesting user.

IAP intercepts the request to the resource and checks to see whether IAP is enabled for the service. If this option is enabled, any IAP credentials that appear in the request headers or cookies are submitted to an IAP authentication server. An OAuth 2.0 Google account sign-in flow that stores a token for future sign-ins is redirected to the user if they do not have browser credentials.

# Advanced Network Security

For GKE and GCE, users can bypass IAP authentication if they can access the VM's application-serving port. IAP-secured applications can't be protected from code executing on a different VM since firewall restrictions can't stop it. A similar aspect applies to Cloud Run, where, if a user has an auto-signed URL, they can bypass the IAP authentication. To safeguard against traffic that does not originate from the serving infrastructure, you must implement firewall rules and a load balancer. Other alternatives, such as using ingress controls for Cloud Run and App Engine, can be used to sign headers.

Next, we will cover how IAP can work to support your on-premises applications' access. There is a new component that will be introduced in the setup, the IAP connector. We will understand what this connector is and also look under the hood of the IAP connector. From an exam perspective, you will not be tested on your knowledge of how an IAP connector works, but it's good to understand it anyway.

![](img/f681dfc12450e3a4c257352b70dbceca_218_0.png)

Figure 8.8 - How IAP for on-premises works

# Identity-Aware Proxy

We will use the illustration given in Figure 8.8 to understand the flow and the key components of IAP for on-premises. We will then look at how secure access is given to applications that are connected via a hybrid connector from Google Cloud to on-premises.

The initial part of the workflow is similar to how IAP works for App Engine, as explained earlier. There is no difference between the authentication and authorization checks that are performed for the user. The request is then sent to the IAP connector, which forwards the request to the on-premises network over a site-to-site connection by Interconnect.

IAP targets on-premises applications with the use of an IAP connector. You can create an IAP connector from the IAM dashboard of the Google Cloud console. An IAP connector is deployed using a configurable Google Cloud Deployment manager. This template deploys the resources that need host and run the IAP connector. Inside your Google Cloud project, the template deploys an Ambassador proxy on a GKE cluster. This proxy is responsible for routing the traffic that is secured by Cloud Identity to your on-premises applications, directly applying Google Cloud Identity and Access Management (Cloud IAM) policies.

You have to define the mappings for the IAP connector. Every routing name must correspond to an ambassador-created GCE backend resource. The mapping parameter has to define the routing with the source and destination. This is to ensure that the requests can be routed from the source to the correct destination, which could be an application on the on-premises network. The following example shows what a mapping should look like:

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

In this example, we route the incoming requests coming from www.crm-domain.com to crm-internal.domain.com and therefore create a mapping for both the host and subdomain as well. Later, we will look at the steps to enable IAP for on-premises applications.

# Advanced Network Security

An important point to note here is IAP by default is integrated with Google identities and uses services such as Google Cloud Identity and Cloud IAM. However, you do have the option to use external identities instead of Google Cloud Identity Platform, which is Google’s customer IAM solution. Google Cloud Identity Platform can be used with IAP. Google Cloud Identity Platform is a completely different product and is not in scope for the exam.

Next, we will look at how to use TCP forwarding for IAP. Use cases are limited to supporting applications that use HTTP or HTTPS. At the time of writing this book, there is no support for thick clients. But you can use TCP forwarding to support both Secure Shell (SSH) and Remote Desktop Protocol (RDP). It is for users to connect to any TCP port on GCE via TCP forwarding, IAP opens a listening port and sends all traffic to the chosen instance. IAP uses HTTPS to encrypt client-side traffic. The gcloud compute ssh encapsulates SSH in HTTPS and passes it to the remote instance. TCP forwarding only works with GCE using IAP and not on-premises.

# Enabling IAP for on-premises

There are four different configurations you should be familiar with: enabling IAP for on-premises apps, enabling IAP for App Engine, enabling IAP for GKE, and enabling IAP for GCE. IAP lets you manage access to services hosted on App Engine, GCE, or an HTTPS balancer. Perform the following steps to configure IAP for App Engine:

1. Open the menu on the left side of the Google console.
2. Click Security.
3. Select Identity-Aware Proxy. The resources of your project are listed on the Identity-Aware Proxy page. If you haven't already, make sure you've configured your OAuth screen.
4. After doing that, come back to the Identity-Aware Proxy page. Follow the steps to configure the consent screen:
   - Go to the OAuth consent screen.
   - Under Support email, select the address you want to display. The email address must belong to the logged-in user account or a Group to which the logged-in user belongs.
   - Enter the application name you want to display.
   - Add any optional details you'd like.
   - Click Save.
5. Navigate back to the Identity-Aware Proxy page and select an app that you want to secure. In the case you don't see your app here, ensure you have App Engine configured. In the case of GCE and GKE, ensure you have a load balancer configured with backends. We covered the ways to create load balancers in Chapter 7, Virtual Private Cloud.

> Note By enabling IAP for your selected app, only the authenticated and authorized members can access it.

6. Select an app by clicking the checkbox on the left side of a row.
7. Turn on the IAP toggle switch for the app you have selected.
8. To confirm that you want your resource to be secured by IAP, click Turn on in the Turn on IAP window that appears.

To control who has access to the app, members need to be given access. In the following step, you will specify the members and assign them appropriate roles to access your app.

9. Click on the Add Member button in the info panel. This opens the Add Member panel. The Add panel temporarily hides the example shared here.
10. In the Add Member panel, enter the users and/or groups in the New members field.
11. Select one of the IAP roles that you want to grant to each new member. These roles are as follows:
    - IAP Policy Admin: Grants administrator rights over Cloud IAP permissions
    - IAP-secured Web App User: Grants access to HTTPS resources that use Cloud IAP
12. Click Save.
