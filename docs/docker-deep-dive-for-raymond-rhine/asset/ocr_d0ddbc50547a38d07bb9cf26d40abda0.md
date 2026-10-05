For example, you might have a microservices app with the following services:

+   * Web front-end
* Ordering
* Catalog
* Back-end datastore
* Logging
* Authentication
* Authorization

Instead of hacking together complex scripts and long `docker` commands, Compose lets you describe the application in a simple YAML file called a `Compose file`. You then use the Compose file with the `docker compose` command to deploy and manage the app.

You should keep your Compose files in a version control system such as Git.

That's the basics. Let's dig deeper.

# Compose background

When Docker was new, a company called `Orchard Labs` built a tool called `Fig` that made deploying and managing multi-