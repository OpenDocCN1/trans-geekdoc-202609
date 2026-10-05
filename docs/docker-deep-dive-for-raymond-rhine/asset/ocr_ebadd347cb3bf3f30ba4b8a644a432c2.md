Non-zero exit codes indicate a failure occurred. Zero exit codes indicate the container exited normally without an error.

We'll demo some examples, but you should also do your own testing.

Let's demonstrate the **always** policy by starting a new interactive container with the **--restart always** flag and telling it to run a shell process. We'll then type **exit** to kill the shell process **and** the container to see what happens.

Run the following command to start an interactive container called **neversaydie** with the **always** restart policy.

```
$ docker run --name neversaydie -it --restart always alpine sh #
```

Your terminal will automatically connect to the shell process inside the container.

Type **exit** to kill the shell process and return to your local terminal. This will cause the container to exit with a zero exit code, indicating a normal exit without any failures.

According to the previous table, the **always** restart policy should automatically restart the container.