available across a modern full-stack application architecture using AWS services:

# Deployment Options Across the Stack

![](bbox=[0.125, 0.203, 0.874, 0.427])

Figure 10.1: AWS deployment options for front end, API, and CI/CD

Let us look at an example of deploying a React App Using S3 + CloudFront.
npm run build

```
aws s3 sync build/ s3://your-bucket-name
aws cloudfront create-invalidation --distribution-id YOUR_ID --paths ""
```

This script performs three key actions:

+   - Builds the React application for production.
- Syncs the compiled build files to an S3 bucket configured for static hosting.
- Invalidates the CloudFront cache to ensure that users receive the latest deployment.

**Copilot and ChatGPT support:** Copilot and ChatGPT enhance the deployment workflow with the following support capabilities:

+   - **GitHub Copilot** streamlines deployment tasks by autocompleting common CLI commands, **package.json**