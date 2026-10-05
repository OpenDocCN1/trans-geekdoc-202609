+   - **docker stop** stops a running container and puts it in the **Exited (137)** state. It issues a SIGTERM to the container’s PID 1 process and allows the container 10 seconds to gracefully quit. If the process hasn’t cleaned up and stopped within 10 seconds, it sends a SIGKILL to force the container to immediately terminate.
- **docker restart** restarts a stopped container.
- **docker rm** deletes a stopped container. You can add the -f flag to delete the container without having to stop it first.
- **docker inspect** shows you detailed configuration and run-time information about a container.
- **docker debug** attaches a debug shell to a container or image and lets you run commands that aren’t available inside the container or image. It requires a Pro, Team, or Business Docker subscription.

# Chapter summary

In this chapter, you learned some of the major differences between VMs and containers, including that containers are smaller, faster, and more portable.

You learned how to start, stop, and restart containers with the **docker** CLI, and you saw that changes to a container’s filesystem persist across restarts.