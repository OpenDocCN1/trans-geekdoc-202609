```
$ docker volume create myvol
myvol
```

By default, Docker creates new volumes with the built-in local driver. And, as the name of the driver suggests, these volumes are only available to containers on the same node as the volume. You can use the -d flag to specify a different driver, but you'll need to install the driver first.

Third-party drivers provide advanced features and access to external storage systems such as cloud storage services and on-premises storage systems such as SAN and NAS. Figure 15.3 shows a Docker host connected to an external storage system via a plugin (driver).

![](bbox=[0.206, 0.606, 0.696, 0.792])

Figure 15.3 Plugging external storage into Docker