
![](img/1c89d4486f90c87568fa6a42d46ae02a_718_0.png)

*Figure 10-1. Navigating to the VPC Service via AWS Management Console Search*

- On the VPC dashboard, click *Create VPC*, as in Figure 10-2.

![](img/1c89d4486f90c87568fa6a42d46ae02a_718_1.png)

*Figure 10-2. VPC Dashboard on AWS*

After clicking “*Create VPC*,” follow these steps from Figure 10-3:

- Choose the VPC with single or multiple public and private subnets.
- Specify the CIDR block (e.g., *10.0.0.0/16*).

![](img/1c89d4486f90c87568fa6a42d46ae02a_719_0.png)

*Figure 10-3. Creating a VPC on AWS*

- For more details, refer to the AWS VPC documentation: `https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html`
- **Create Subnets:**
    - Navigate to the Subnets section within the VPC dashboard, as shown in Figure 10-4.

![](img/1c89d4486f90c87568fa6a42d46ae02a_720_0.png)

*Figure 10-4. Navigating to the Subnets Section Within the VPC Dashboard on AWS*

- Click "Create subnet" as in Figure 10-5.

![](img/1c89d4486f90c87568fa6a42d46ae02a_721_0.png)

*Figure 10-5. Creating a Subnet on AWS*

- Create at least two private subnets in different Availability Zones.
- Name your subnets for easy identification (e.g., Private-Subnet-1 and Private-Subnet-2).
- Repeat the process to create public subnets for NAT gateways.
- For more details, refer to the AWS documentation: `https://docs.aws.amazon.com/vpc/latest/userguide/how-it-works.html`
- **Create and Attach the Internet Gateway:**
    - Navigate to the Internet gateways section.
    - Click "Create internet gateway."
    - Attach the Internet gateway to your VPC by selecting "Actions" and choosing "Attach to VPC."
- For more details, refer to the AWS "Enable VPC internet access using internet gateways" documentation: `https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html#Add_IGW_Attach_Gateway`
- **Create the NAT Gateway:**
    - Navigate to the NAT gateways section as shown in Figure 10-6.

![](img/1c89d4486f90c87568fa6a42d46ae02a_723_0.png)

*Figure 10-6. Navigating to the NAT gateways Section on AWS*

- Click “Create NAT gateway” as in Figure 10-7.

![](img/1c89d4486f90c87568fa6a42d46ae02a_724_0.png)

*Figure 10-7. Creating a NAT Gateway on AWS*

- Select the public subnet where the NAT gateway will be created.
- Allocate an Elastic IP to the NAT gateway.
- For more details, refer to the AWS NAT gateways documentation: `https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html`
- **Update Route Tables:**
    - Navigate to the Route tables section.
    - Update the route tables of your private subnets to route Internet-bound traffic through the NAT gateway.
    - For more details, refer to the AWS “Configure route tables” documentation: `https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html`
- **Configure Security Groups:**
    - Navigate to Security groups as in Figure 10-8.

![](img/1c89d4486f90c87568fa6a42d46ae02a_725_0.png)

*Figure 10-8. Navigating to Security Groups in AWS VPC Dashboard*

- Create security groups with the necessary inbound and outbound rules for your MWAA environment.
- Associate these security groups with your MWAA environment during its creation.
- For more details, refer to the AWS “Control traffic to your AWS resources using security groups” documentation: `https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html`

**Step 7: Configure Environment Class**

- Choose the appropriate instance class for your MWAA environment. This determines the compute resources allocated to your environment.
- Specify the maximum number of workers for your environment.
- Specify the minimum number of workers for your environment.
- Define the number of schedulers.
- Add any custom configurations for Airflow.
- Specify any custom plugins by providing the S3 path.
- Provide the S3 path to the requirements.txt file for additional Python dependencies.
- Review all the configurations you have set.
- Click the “Create environment” button to create your MWAA environment.
- The creation process may take a few minutes.
- You can monitor the status of your environment on the Amazon MWAA dashboard.

Once the environment is created and the status is active, you can start deploying and managing your DAGs using the specified S3 bucket and folder.

## Step 2: Developing the DAG

After setting up the Amazon MWAA environment, the next step is to develop the DAG. Let’s develop a simplified DAG (`simple_mwaa_dag.py`) for illustration purposes. This provides a foundational understanding of how to define tasks, set task dependencies, and execute Python functions within Airflow.

The DAG below defines default arguments, the DAG itself, Python functions for tasks, and tasks and sets task dependencies. The DAG executes two Python tasks: one to print the current date and time and another to print a predefined message. When orchestrated by Airflow, these tasks ensure that they execute in a defined sequence:

```python
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from datetime import datetime, timedelta

# Define default arguments

default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2023, 1, 1),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

# Define the DAG

dag = DAG(
    'simple_mwaa_dag',
    default_args=default_args,
    description='A simple DAG for MWAA',
    schedule_interval=timedelta(days=1),
)
```

```python
# Define Python functions for tasks

def print_current_date():
    print(f"Current date and time: {datetime.now()}")

def print_message():
    print("Hello, this is a message from your DAG!")
```

```python
# Define tasks

t1 = PythonOperator(
    task_id='print_date',
    python_callable=print_current_date,
    dag=dag,
)

t2 = PythonOperator(
    task_id='print_message',
    python_callable=print_message,
    dag=dag,
)
```

```python
# Set task dependencies

t1 >> t2
```

The DAG starts with the ‘print_date’ task, which utilizes a PythonOperator to execute the “print_current_date” function. Inside this function, the current date and time are retrieved using Python’s `datetime.now()` function, and this information is printed to the Airflow logs. Once the ‘print_date’ task completes successfully, Airflow proceeds to the ‘print_message’ task. Similar to the previous task, it uses a PythonOperator to execute the “print_message” function. Inside this function, a simple message, “Hello, this is a message from your DAG!”, is printed to the Airflow logs.

These tasks are linked together with a task dependency, indicated by the `>>` operator, ensuring that the ‘print_message’ task runs only after the ‘print_date’ task has successfully completed. This dependency ensures a logical sequence of task execution within the DAG.

## Step 3: Uploading to S3

After DAG development, the next step is to deploy the DAG to Amazon MWAA. The first task in this deployment is to upload the file containing the DAG to an Amazon S3 bucket that is accessible by the Amazon MWAA environment. The command below uploads the `simple_mwaa_dag.py` DAG file from `/home/ubuntu/airflow/dags/` directory on Amazon EC2 to the `dags` folder within the `instance1bucket` S3 bucket:

```bash
aws s3 cp /home/ubuntu/airflow/dags/simple_mwaa_dag.py \
      s3://instance1bucket/dags/
```

DAG files and their dependencies are usually packaged into a zip file before loading into an S3 bucket. In this simple example, the DAG file (`simple_mwaa_dag.py`) does not have any external dependencies; hence, there is no need to package it into a zip file for deployment. However, as the complexity of DAGs increases and external dependencies such as custom Python modules or third-party libraries are introduced, packaging DAGs into zip files becomes essential.

A good example of a complex DAG is the `tesla_stock_prediction` DAG we developed in Chapter 8. In this chapter, we created an Airflow pipeline that included preprocessing Tesla stock data using PySpark and building, training, and evaluating a deep learning model using PyTorch to predict the Tesla stock price. The DAG has the following five modules:

- `data_processing.py`: Preprocesses the Tesla stock data
- `model_training.py`: Utilizes the PyTorch library to create and train the neural network regression model for the Tesla stock price prediction
