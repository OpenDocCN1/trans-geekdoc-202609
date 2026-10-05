Mac OS Darwin kernel. This is why it shows as `darwin/amd64` or `darwin/arm64`.

You can now use Docker on your Mac.

# Installing Docker with Multipass

Only consider this section if you can't use Docker Desktop, as Multipass installations don't ship with out of the box support for `docker scout`, `docker debug`, or `docker init`.

Multipass is a free tool for creating cloud-style Linux VMs on your Linux, Mac, or Windows machine and is incredibly easy to install and use. It's an easy way to create multi-node production-like Docker clusters.

Go to `https://multipass.run/install` and install the right edition for your hardware and OS.

Once installed, you only need three commands:

```
$ multipass launch
$ multipass ls
$ multipass shell
```

Let's see how to launch and connect to a new VM with Docker pre-installed.