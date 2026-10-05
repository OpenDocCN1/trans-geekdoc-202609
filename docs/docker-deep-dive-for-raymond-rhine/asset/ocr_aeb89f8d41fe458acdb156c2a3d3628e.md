Notice how it started much faster this time. This is because the volume and both images already exist.

Check the current state of the app with the `docker compose ps` command.

| NAME | COMMAND | SERVICE | STATUS |
| --- | --- | --- | --- |
| multi-container-redis-1 | "docker-entrypoint." | redis | Up |
| multi-container-web-fe-1 | "python app/app.py" | web-fe | Up |

The output shows both containers, the commands they're executing, their current state, and the network ports they're listening on.

Run a `docker compose top` to list the processes inside each container.

```
$ docker compose top
multi-container-redis-1
UID PID PPID ... CMD
lxd 12023 11980 redis-server **:6379

multi-container-web-fe-1
UID PID PPID ... CMD
root 12024 12002 0 python app/app.py python app.py
root 12085 12024 0 /usr/local/bin/python app/app.py python
```