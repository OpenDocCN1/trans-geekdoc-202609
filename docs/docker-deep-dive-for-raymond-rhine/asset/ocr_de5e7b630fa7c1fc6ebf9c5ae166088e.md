lightweight council to govern container standards. This allowed us to archive the appc project and place all low-level container-related specifications under the OCI governance.

At the time of writing, the OCI maintains three standards called specs:

+   - The image-spec
- The runtime-spec
- The distribution-spec

We often use a rail tracks analogy when explaining the OCI standards:

When the size and properties of rail tracks were standardized, it gave entrepreneurs in the rail industry confidence the trains, carriages, signaling systems, platforms, and other rail infrastructure they built would work with the standardized tracks — nobody wanted competing standards for track sizes.

The OCI specifications did the same thing for the container ecosystem and it's flourished ever since. Docker has also changed a lot since the formation of the OCI, and all modern versions of Docker implement all three OCI specs. For example:

+   - The Docker builder (BuildKit) creates OCI compliant-images