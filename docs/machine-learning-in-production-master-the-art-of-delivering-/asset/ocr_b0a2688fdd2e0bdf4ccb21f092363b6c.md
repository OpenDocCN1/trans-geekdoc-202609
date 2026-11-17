# Objectives

After studying this chapter, you should be able to deploy the ML model on Heroku - Platform as a Service (PaaS) and integrate the GitHub repository into Heroku for automated deployment. Create the Heroku app from Heroku web UI and the terminal. You will learn to build and run CI/ CD pipelines using GitHub Actions and Heroku. You will also learn to execute multiple tests using pytest and tox on GitHub Actions. Create YAML files for GitHub Actions to run the workflow.

# Heroku

Heroku is a container-based cloud Platform as a Service (PaaS) platform. Developers use Heroku to deploy, manage, and scale modern apps. It has a pretty easy process to deploy your applications.

Heroku saves you time by removing the difficulty of maintaining servers, hardware, or infrastructure. It supports the most popular languages, such as Node, Ruby, Java, Clojure, Scala, Go, Python, and PHP.

Simply put, Heroku allows you to make your apps available on the internet for others to access, like a website. With a few steps, it allows you to make your app accessible to others. You can focus on app development without worrying about infrastructure, servers, and other such things.

It enables easy integration with GitHub to make it easy to deploy code available on the GitHub repository to apps that are running on Heroku. When GitHub integration is configured for a Heroku app, Heroku can automatically build and release (if the build is successful) the updates when pushed to the specified repository.

Heroku apps can be scaled to run on multiple dynos (a container that runs a Heroku app’s code) simultaneously (except on Free or Hobby dynos) with simple steps to avoid any downtime. Heroku offers manual and auto scaling of the dynos. You can scale it horizontally by adding more dynos to handle the heavy traffic of requests. On the other hand, you can scale it vertically by increasing resources like memory and CPU as required.

Heroku offers Continuous Integration and Continuous Deployment. It has built-in test facilities to achieve Continuous Deployment. Heroku apps that share the same codebase can be organized into deployment pipelines, promoted easily from one stage to the next, and managed through a visual interface.

There are three methods to deploy the web app on the Heroku platform:

+   - Deployment with Heroku git

+   - Deployment with GitHub repository integration