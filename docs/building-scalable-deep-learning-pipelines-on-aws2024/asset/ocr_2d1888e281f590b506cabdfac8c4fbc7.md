+   4. Trigger the DAG: After the web server and scheduler are running, trigger the DAG using the Airflow command-line interface (CLI):

    ```
    [In]: airflow dags trigger taco_prices_dag
    ```

    This command triggers the execution of the taco_prices_dag DAG.

Before diving deeper into the code and explaining each component of the DAG in more detail, it’s important to note that Apache Airflow offers several deployment options, each suited to different environments and requirements. The one discussed here is the standalone deployment option, where Airflow, as will be examined in more detail in the next chapter (“Setting Up a Deep Learning Environment on AWS”), is installed and run directly on a single machine. This setup is straightforward and ideal for testing. It is popular among individual developers and small teams working on less complex DAGs. Although standalone Airflow is easy to set up and requires fewer resources, it comes with limitations such as limited scalability, making it less suitable for larger production environments.

In the next chapter, we also examine the second option—a Docker containerized setup, where Airflow runs in isolated Docker containers. This method provides more flexibility and scalability than a standalone deployment. Using Docker, Airflow and its dependencies are packaged into containers, ensuring consistent environments across development, staging, and production. This setup is ideal for teams that need to manage dependencies, avoid conflicts, and easily scale their Airflow environment by adding more containers.

In Chapter 10, we explore a third option: Amazon Managed Workflows for Apache Airflow (MWAA), a fully managed service provided by AWS. MWAA takes care of the setup, scaling, and maintenance of Airflow, allowing users to focus solely on writing and running their DAGs. This option is best suited for production environments that require high availability, reliability, and seamless integration with other AWS services.