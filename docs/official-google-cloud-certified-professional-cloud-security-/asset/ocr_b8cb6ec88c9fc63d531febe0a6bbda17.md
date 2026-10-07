+   III. Enter the application name you want to display.

+   IV. Add any optional details you'd like.

+   V. Click Save.

+   5. Navigate back to the Identity-Aware Proxy page and select an app that you want to secure. In the case you don't see your app here, ensure you have App Engine configured. In the case of GCE and GKE, ensure you have a load balancer configured with backends. We covered the ways to create load balancers in Chapter 7, Virtual Private Cloud.

> Note
By enabling IAP for your selected app, only the authenticated and authorized members can access to it.

+   6. Select an app by clicking the checkbox on the left side of a row.

+   7. Turn on the IAP toggle switch for the app that you have selected.

+   8. To confirm that you want your resource to be secured by IAP, click Turn on in the Turn on IAP window that appears.

To control who has access to the app, members need to be given access. In the following step, you will specify the members and assign them appropriate roles to access your app.

+   9. Click on the Add Member button in the info panel. This opens the Add Member panel. The Add panel temporarily hides the example shared here.

+   10. In the Add Member panel, enter the users and/or groups in the New members field.

+   11. Select one of the IAP roles that you want to grant to each new member. These roles are as follows:

+   I. IAP Policy Admin: Grants administrator rights over Cloud IAP permissions

+   II. IAP-secured Web App User: Grants access to HTTPS resources that use Cloud IAP

+   12. Click Save.