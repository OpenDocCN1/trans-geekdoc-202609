execute Heroku commands through the local terminal. At this stage, create one more app for production, and name it docker-ml-cicd-prod.
At this stage, your Heroku account should be ready with the apps you have created.

# # Deployment with Heroku Git

This method is pretty much straightforward. You need Heroku CLI for this method. Add Heroku’s Git remote repository and push the changes to it directly.

From the Heroku application dashboard, go to the **Deploy** tab. You will see three methods of deployment there:

+   - Heroku Git
+   - GitHub
+   - Container Registry

The following figure shows the deployment methods available on the Heroku platform:

![](bbox=[0.19, 0.48, 0.81, 0.57])

Figure 10.2: Deployment method

From the preceding methods, you need to select the first method, that is, the Heroku Git method, and follow the steps given below that option.

# # Deployment with GitHub repository integration

Heroku comes with the GitHub integration method, which enables you to automate the deployment process. Post GitHub and Heroku integration, any changes pushed to the repository will trigger the process that deploys the Heroku app at the end.

On Heroku, you can create a pipeline and add both apps to it. Heroku allows you to create review (temporary) apps before deploying the staging app. This additional option enables you to see the working of the app before pushing it to the staging or pre-deployment stage.