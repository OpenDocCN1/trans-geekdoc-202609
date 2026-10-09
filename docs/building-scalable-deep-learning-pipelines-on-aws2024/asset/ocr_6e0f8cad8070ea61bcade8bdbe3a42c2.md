# # Installing Airflow

There are three primary options for using Apache Airflow on EC2: standalone, Docker-based, and fully managed through Amazon Managed Workflows for Apache Airflow (MWAA). In this section, we provide instructions for setting up the standalone and Docker-based versions of Airflow, while guidance on using MWAA will be provided in Chapter 10.

# ## Standalone Installation

In this subsection, detailed instructions are provided for setting up Airflow on an EC2 instance using a standalone installation. This setup allows for direct control over the Airflow environment without additional layers of abstraction.

Follow these steps to perform this installation:

Step 1: Activate your environment:

```
[In]: source /home/ubuntu/myenv/bin/activate
```

Step 2: Update and install dependencies:

```
[In]: sudo apt update
[In]: sudo apt install python3-pip sqlite3 libpq-dev
```

+   * `sudo apt update`: This command updates the package lists for upgrades.
* `sudo apt install python3-pip sqlite3 libpq-dev`: Installs necessary dependencies including Python 3 pip, SQLite, and PostgreSQL development files.