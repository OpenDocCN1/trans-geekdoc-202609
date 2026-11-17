# # CHAPTER 10

# # Deploying ML Models on Heroku

# ## Introduction

Heroku is a **Platform as a Service (PaaS)** platform that enables developers to build, run, and operate applications entirely in the cloud. You can push the Docker container to Heroku or provide GitHub repository details, such as the branch name, to auto-deploy the web app as soon as you push new changes to the model. This way, you can make the ML model accessible on the web, ready to make predictions.

If you are a beginner, then GitHub CI/CD is the simplest platform to build an end-to-end CI/CD pipeline. It is easy to manage as everything is in GitHub. You only need a GitHub repository to create and run a GitHub Actions workflow.

Refer to the previous chapters for the concepts discussed, such as packaging ML models, FastAPI, docker, and CI/CD pipeline.

# ## Structure

This chapter discusses the following topics:

+   - Create a Heroku account and install Heroku CLI
+   - Create a Heroku app
+   - Deploy the web app to Heroku using Heroku CLI
+   - Build CI/CD pipeline using GitHub Actions