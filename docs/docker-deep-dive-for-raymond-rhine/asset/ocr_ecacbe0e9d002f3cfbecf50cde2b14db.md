+   docker compose stop will stop all containers in a Compose app without deleting them from the system. You can easily restart them with docker compose restart , and you shouldn't lose any data.

+   docker compose restart will restart a stopped Compose app. If you make changes to the Compose file while it's stopped, these changes will not appear in the restarted app. You need to redeploy the app to see any changes you made in the Compose file.

+   docker compose ps lists each container in the Compose app. It shows the current state, the command each container is running, and network ports.

+   docker compose down will stop and delete a running Compose app. By default, it deletes containers and networks but not volumes and images.

# Chapter Summary

In this chapter, you learned how to deploy and manage multi-container applications using Docker Compose.

Compose is now fully integrated into the Docker Engine and has its own docker compose sub-command. It lets you define multi-container applications in declarative configuration files and deploy them with a single command.