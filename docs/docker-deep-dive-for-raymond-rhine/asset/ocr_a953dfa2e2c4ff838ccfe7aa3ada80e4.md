# 2. Runtime Specification (runtime-spec)

Both specifications were released as version 1.0 in July 2017 and are still vital today.

They've even added a third specification called the Distribution Specification (distribution-spec) governing how images are distributed via registries.

At the time of writing, the runtime-spec is at version 1.1.0, the image-spec is at version 1.0.2, and the distribution-spec is at 1.0.1. However, plans are underway for version 1.1 of both the image-spec and distribution-spec. We mention this to highlight the slow-steady nature of these low-level specifications are heavily relied upon by so many other projects — stability is the name of the game for low-level OCI specs.

Docker, Inc. was a founding member of the OCI and was heavily involved in defining the specifications. It continues to be involved by contributing code and helping guide the specifications.

All versions of Docker since 2016 have implemented the OCI specifications. For example, Docker uses runc, the reference implementation of the OCI runtime-spec, to create OCI-compliant containers (runtime-spec). It also uses BuildKit to