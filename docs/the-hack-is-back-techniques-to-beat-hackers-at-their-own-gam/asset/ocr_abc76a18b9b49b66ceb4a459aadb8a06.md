The LOTS project has several different websites and helps users understand not only how to create websites from these trusted sites, but also how to detect them. We can use this project to help us choose where and how we want to host our services to try and blend into trusted websites. This can be exceptionally effective when we’re planning out how to protect our infrastructure while it’s being created.

# API GATEWAYS

Within recent years, many cloud providers have started to allow different ways for us to redirect traffic through their API gateways. This can be a convenient way for us to leverage these LOTS websites while redirecting our target traffic into our C2. The API gateway is designed as a service to be an intermediary between an application and a backend service—we can abuse this functionality to choose where we want the cloud service to direct a specific payload to route the traffic.

# Azure API Gateways

We can establish an API gateway within Azure relatively easily. This is achieved within the Azure API Management page from the Azure Portal. Clicking on this page will open up the API Management location where we can create a gateway.

![](bbox=[0.106, 0.407, 0.894, 0.694])

**FIGURE 4.9**  Within the Azure Portal, navigating to the API Management Services.

On the next page, select **Create** to make a new API. Then we can fill out the information to create our API Gateway, including creating the specific subdomain that will be used. In the example below, we’ve used the name **really-important-dont-delete** which is intended to give a perception