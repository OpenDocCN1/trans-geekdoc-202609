Check the builds and image sizes.

| REPOSITORY | TAG | IMAGE ID | CREATED | SIZE |
|---|---|---|---|--|
| multi | full | a7a01440f2b5 | 4 hours ago | 25.2MB |
| multi | server | a75778df1b9c | 4 seconds ago | 11.7MB |
| multi | client | 02b621e9415f | 37 seconds ago | 11.9MB |

You now have three images, and the **client** and **server** images are each about half the size of the **full** image. This makes sense because the **full** image contains the client and server binaries, whereas the others only include one.

# Buildx, BuildKit, drivers, and Build Cloud

This section takes a quick look at the major components that power builds.

Behind the scenes, Docker's build system has a client and server:

+   - **Client**: Buildx
- **Server**: BuildKit

Buildx is Docker's latest and greatest build client. It's implemented as a CLI plugin and supports all the latest features of BuildKit, such as multi-stage builds, multi-architecture