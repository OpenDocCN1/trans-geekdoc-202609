containers. However, configuring your own requires extensive effort and testing.

# Mandatory Access Control systems

Docker works with major Linux MAC technologies such as AppArmor and SELinux.

Depending on your Linux distribution, Docker applies default AppArmor or SELinux profiles to all new containers, and according to the Docker documentation, the default profiles are moderately protective while providing wide application compatibility.

You can tell Docker to start containers without these policies, and you can configure your own. However, with capabilities, configuring your own policies is very powerful but requires a lot of effort and testing.

# seccomp

Docker uses seccomp to limit which syscalls a container can make to the host's kernel.

Syscalls are how applications ask the Linux kernel to perform tasks. At the time of writing, Linux has over 300 syscalls and the