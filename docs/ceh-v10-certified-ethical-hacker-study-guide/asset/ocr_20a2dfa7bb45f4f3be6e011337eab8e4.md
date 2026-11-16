access programmatically. It maintains some level of accountability and prevents the service from being overused or misused.

# Twitter

Another common social networking site or service is Twitter. There is a lot posted to Twitter that can be of some use. Again, programmatic access to Twitter is useful. You can search using the regular interface, but it's sometimes helpful to be able to use other tools. In order to gain access to Twitter programmatically, you need to get an API key. This means you need to tell Twitter you are creating an application. You can easily tell Twitter you are creating an application without any special credentials through the Twitter developer's website. When you go through the process to create an application, what you are doing is creating identification information that your app needs to interact with the Twitter service. In Figure 4.11, you can see keys and access tokens for an app.

# FIGURE 4.11 Twitter keys and access tokens

![](bbox=[0.2, 0.39, 0.71, 0.67])

What you may notice in Figure 4.11 is that the app is named recon-ng-me. The reason for this is that I created the app just to get the key and token so I could add it into recon-ng, a tool used for reconnaissance that includes many plug-ins. Some of these plug-ins require API keys or access tokens in order to be able to interact with the service being queried. That's the case with the Twitter plug-in. In the following code, you can see the list of API keys that recon-ng uses and the API keys set for Twitter.