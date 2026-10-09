+   - Start the Airflow web server again:

```
`[In] : airflow webserver &`
```

# ## Docker-Based Setup

Running Apache Airflow in Docker offers significant advantages over a traditional standalone installation, providing a streamlined, consistent environment that simplifies setup, reduces configuration errors, and enhances portability. Docker encapsulates Airflow and its dependencies within containers, ensuring reliable workflow execution across different systems, whether in development, testing, or production.

To set up Apache Airflow in Docker, you need to install Docker and Docker Compose. Docker packages applications into containers, including all necessary code, libraries, and dependencies, ensuring consistency across various environments. Docker Compose further simplifies this by allowing you to define and manage multi-container applications, which is particularly useful for complex setups like Apache Airflow, where services such as the web server, scheduler, and database must work together.

The Apache Airflow project provides an official `docker-compose.yml` file that defines all the required services, including the Airflow web server for workflow management, the scheduler for task execution, Postgres for metadata storage, Redis for task queue management, and workers and triggerers for executing tasks and handling deferred operations.

The easiest way to install Docker on a Linux operating system, such as Ubuntu, for testing purposes is to use the convenience script provided by Docker at `https://get.docker.com/`. After installing Docker on your EC2 instance, you set up and run Airflow using the official Docker Compose configuration.