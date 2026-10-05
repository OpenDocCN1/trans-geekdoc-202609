Compose files define all the containers, networks, volumes, secrets, and other configurations an application needs. You then use the docker compose command to post the Compose file to Docker, and Docker deploys it.

Once you’ve deployed the app, you can manage its entire lifecycle using docker compose sub-commands.

Docker Compose is popular with developers, and the Compose file is an excellent source of application documentation — it defines all the services that make up the app, the images they use, the ports they expose, the networks and volumes they use, and much more. As such, it can help bridge the gap between development and operations teams. You should also treat Compose files as code and store them in version control systems.