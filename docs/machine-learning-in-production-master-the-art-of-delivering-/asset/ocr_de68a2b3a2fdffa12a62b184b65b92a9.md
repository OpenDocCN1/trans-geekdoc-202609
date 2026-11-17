![](bbox=[0.13, 0.1, 0.87, 0.44])

Figure 12.4: Code files pushed to Cloud Source Repository

# Cloud Build

Cloud Build is a serverless platform that allows users to automate build, test, and deploy containers in the cloud quickly. Cloud Build works with deployment environments of the App Engine, Kubernetes Engine, Cloud Run, Cloud Functions, and Firebase. It will charge you for build minutes that are utilized if your usage exceeds the free quota allotted by GCP.

Cloud Build config file type can be YAML or JSON. This file contains a series of steps and commands to execute the build, specified by the developer. Each build step runs in its own Docker container. However, these containers are connected through a local Docker network with a Cloud Build. This permits build steps to communicate and share information.

Search and enable Cloud Build API in APIs and services. Cloud Build uses a special service account to execute builds on your behalf. The email format of the Cloud Build service account is [PROJECT_NUMBER]@cloudbuild.gserviceaccount.com. It has permission to execute tasks like fetching code from the repository, getting project details, and writing objects to storage associated with the project. However, this default service account can be changed to the developer's own service account to execute builds on the developer's behalf, and the developer can set specific permissions.