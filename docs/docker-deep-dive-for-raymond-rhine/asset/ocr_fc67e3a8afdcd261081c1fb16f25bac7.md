# 16: Docker security

If security is hard, we’re less likely to implement it. Fortunately, most of the security in Docker is easy and pre-configured with sensible defaults. This means you get a moderately secure experience with zero effort. The defaults are not perfect, but they’re a good starting point.

Docker supports all major Linux security technologies and adds some of its own. As such, I’ve divided the chapter so we cover the Linux security technologies first and finish the chapter covering the Docker technologies:

+   * Docker security – The TLDR
* Linux security technologies
  * Kernel namespaces
  * Control Groups
  * Capabilities
  * Mandatory Access Control
  * seccomp
* Docker security technologies
  * Swarm security
  * Docker Scout and vulnerability scanning
  * Docker Content Trust
  * Docker secrets