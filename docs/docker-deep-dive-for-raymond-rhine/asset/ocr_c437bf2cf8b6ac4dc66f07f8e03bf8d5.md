This application tells Docker to update two replicas at a time, wait 10 seconds between each set of two, and perform a rollback if it encounters any problems.

Rolling back replaces the new replicas with fresh copies of the old version. The default value for failure_action is pause, which will halt the update where it is and may result in some replicas running the old version and some running the new. The other option is continue.

The deploy.placement block forces all replicas onto worker nodes. You'll need to delete this section if you're running a single-node cluster with one manager and zero workers.

```
web-fe:
  deploy:
    placement:
      constraints:
        - 'node.role == worker'
```

The deploy.restart_policy block tells Docker what to do when it encounters a failure during a rollout.

```
web-fe:
  deploy:
    restart_policy:
```