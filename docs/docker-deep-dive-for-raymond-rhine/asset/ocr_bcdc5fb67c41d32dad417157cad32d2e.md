Unfortunately, Windows images can be huge. For example, some Windows-based images can be gigabytes in size and take a long time to push and pull.

# Pulling images

A clean Docker installation has an empty local repository.

Local repository is jargon for an area on your local machine where Docker stores images for more convenient access. We sometimes call it the image cache, and on Linux it’s usually located in /var/lib/docker/<storage-driver>. However, it will be inside the Docker VM if you're using Docker Desktop.

Run the following command to inspect the contents of your local repository. This example has three images relating to three Docker Desktop extensions I’m running. Yours will be different and may be empty.

| REPOSITORY | TAG | IMAGE ID | CREATED |
|---|---|---||
| docker/disk-usage-extension | 0.2.9 | f4c95478a537 | 2 weeks ago |
| docker/logs-explorer-extension | 0.2.6 | 417dd9a8f96d | 2 months ago |
| portainer/portainer-docker-extension | 2.19.4 | 908d04d20e86 | 2 months ago |

The process of getting images is called *pulling*.