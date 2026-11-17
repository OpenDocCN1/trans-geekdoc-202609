+   • Deployment with Container Registry

Now that you must have got the gist of it, you are going to deploy a Machine Learning model to Heroku. After studying this chapter, you will be in a better position to work on Heroku for ML deployments.

# # Setting up Heroku

You need to create a Heroku account. This is a one-time activity. Go to the Heroku platform at https: // www.heroku.com /

**Step 1:**
Create a Heroku account (if you don’t have one) and log in.

Select the primary development language as **Python** and create a free account.

**Step 2:**
After logging in to the account, create a new app, as shown in the following figure:

![](bbox=[0.405, 0.45, 0.62, 0.56])

*Figure 10.1: Create a new app*

Click on the **Create new app** button and add the app name. In this case, it is **docker-ml-cicd**.

Hit the **Create app** button and complete the process.

> > Note: Two or more Heroku apps can’t have the same name.

**Step 3:**
You can click the **Open app** button to see the app. For the current scenario, it is https: // docker-ml-cicd.herokuapp.com /

It will display the following text:

**Heroku | Welcome to your new app!**

Now, go back to your Heroku app dashboard and install the Heroku **Command Line Interface (CLI)** for ease of access through the terminal. Heroku’s CLI installation steps are mentioned at https: // devcenter.heroku.com / articles / heroku-cli. You can