COPY . /src against the AAA image. However, if the files that the COPY . /src instruction copies into the layer have changed since the cached layer was built, you cannot use the cached layer as you'd get old versions of the files. To protect against this, Docker performs checksums against each file it copies. If the checksums don't match, the cache is invalidated, and Docker builds a new layer.

# Only install essential packages

We often joke that we install the entire internet when we build apps. As a quick example, the simple Node.js app used earlier in the chapter depends on two packages:

+   - Express
- Pug

However, these packages depend on other packages, which in turn depend on others. At the time of writing, building this simple application with two dependencies actually downloads 97 packages!

Fortunately, some package managers provide a way for you to only download and install essential packages instead of the entire internet. One example is the apt package manager that lets you specify the no-install-recommends flag so that it