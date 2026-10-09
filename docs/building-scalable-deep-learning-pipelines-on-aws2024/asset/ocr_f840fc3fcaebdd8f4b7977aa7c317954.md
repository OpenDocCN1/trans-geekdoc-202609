policies within the Airflow instance. Admin users have the authority to
configure access controls, set permissions, and monitor user activity,
ensuring the integrity and security of the Airflow environment.

Step 9: Start Airflow web server and scheduler:

```
[In]: airflow webserver &
[In]: airflow scheduler
```

+   airflow webserver &: This command starts the Airflow
web server in the background. The web server provides
a user interface (UI) for managing and monitoring
Airflow workflows. By running the web server in the
background with the & symbol, you allow it to continue
running even after you log out of the terminal session.
This ensures that the web UI remains accessible even
when you are not actively logged into the server.

+   airflow scheduler: This command starts the Airflow
scheduler. The scheduler is responsible for triggering
task instances based on the defined schedule (e.g., cron
expressions) and dependencies between tasks (defined
in Directed Acyclic Graphs or DAGs). It continuously
monitors the DAGs for tasks that need to be executed
and triggers them according to their schedule and
dependencies.

It’s recommended to run these commands in separate terminal
sessions. Running them separately allows for better monitoring and
troubleshooting of each component. Tools like tmux or screen provide
session management features, enabling you to detach and reattach to
terminal sessions, ensuring that the web server and scheduler continue
running even after you log out of the terminal session.