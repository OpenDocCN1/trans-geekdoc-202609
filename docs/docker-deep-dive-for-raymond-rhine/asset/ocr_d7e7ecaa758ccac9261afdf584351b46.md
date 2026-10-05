```
}
```

You can also start a container or a service with the --log-driver and --log-opts flags to override the settings in daemon.json.

Container logs work on the premise that your application runs as PID 1 and sends logs to STDOUT and errors to STDERR . The logging driver then forwards everything to the locations configured via the logging driver.

The following is an example of running the docker logs command against a container called vantage-db that is configured with the json-file logging driver.

```
$ docker logs vantage-db
1:C 2 Feb 09:53:22.904 # o000o000o000 Redis is starting o0000000
1:C 2 Feb 09:53:22.904 * Redis version=4.0.6, bits=64, commit=000
1:C 2 Feb 09:53:22.904 * Warning: no config file specified, using
1:M 2 Feb 09:53:22.906 * Running mode=standalone,port=6379.
1:M 2 Feb 09:53:22.906 * WARNING: The TCP block setting of 511
1:M 2 Feb 09:53:22.906 # Server initialized
1:M 2 Feb 09:53:22.906 # WARNING overcommit_memory is set to 0!
```

There’s a good chance you’ll find network connectivity errors in the daemon logs or container logs.