
3. Choose the service that will use this role (in this case, EC2).
4. Attach the necessary policies that grant permissions to access S3 resources (e.g., AmazonS3FullAccess for full access).
5. Review and name your role and then create it.
6. Navigate to the EC2 Dashboard in the AWS Management Console.
7. Select the EC2 instance to which you want to attach the IAM role.
8. Click “Actions” ➤ “Security” ➤ “Modify IAM role.”
9. Select the IAM role you created earlier from the dropdown menu and confirm the attachment.
10. Once the IAM role is attached to your EC2 instance, you can access S3 data programmatically using AWS SDKs or command-line tools like the AWS CLI.

## Creating a Project Directory

After provisioning an Amazon EC2 instance, creating a project directory is a logical step. This is important for organizing and managing your work efficiently. It provides a structured environment to store all project-related files, including source code, data, documentation, and outputs, facilitating ease of navigation and collaboration. With a designated directory, version control becomes more straightforward, ensuring that changes are tracked accurately and collaboration flows smoothly. Additionally, a well-organized project directory enhances reproducibility by encapsulating all necessary files and dependencies, making it easier to share and replicate results across different environments. It also promotes scalability and maintenance, allowing new components to be added without compromising the overall organization. Ultimately, a project directory serves as a foundation for effective project management, documentation, and collaboration, contributing to the success of your project.

In the previous chapter, we outlined a directory structure for a Tesla stock prediction project, but we didn’t delve into the code that generated it. The Bash script below, which was executed within JupyterLab in a notebook environment on EC2, establishes this structure with specific subdirectories and files necessary for organizing data, source code, and output files. The tree command at the end displays the structure of the created directories for visual representation:

```bash
%bash
project_dir="Project Directory Structure"
mkdir -p "$project_dir"
mkdir -p "$project_dir/data"
touch "$project_dir/data/TSLA_stock.csv"
mkdir -p "$project_dir/src/pyspark_code"
touch "$project_dir/src/main.py"
touch "$project_dir/src/pyspark_code/data_preprocessing.py"
mkdir -p "$project_dir/src/pytorch_code"
touch "$project_dir/src/pytorch_code/model.py"
touch "$project_dir/src/pytorch_code/model_training.py"
mkdir -p "$project_dir/output"
mkdir -p "$project_dir/output/TSLA_stock.parquet"
touch "$project_dir/output/TSLA_stock.parquet/_SUCCESS"
touch "$project_dir/output/TSLA_stock.parquet/part-00000-2c717885-1e92-4091-b73e-c07fb2f42ba8-c000.snappy.parquet"
mkdir -p "$project_dir/output/TSLA_stock_train.parquet"
touch "$project_dir/output/TSLA_stock_train.parquet/_SUCCESS"
touch "$project_dir/output/TSLA_stock_train.parquet/part-00000-3931d223-097a-4b7f-a6df-6ddc8abfcb5c-c000.snappy.parquet"
mkdir -p "$project_dir/logs"
mkdir -p "$project_dir/tests"
touch "$project_dir/tests/test.py"
mkdir -p "$project_dir/visualizations"
touch "$project_dir/visualizations/plot.png"
touch "$project_dir/README.md"
touch "$project_dir/config.yaml"
touch "$project_dir/requirements.txt"
tree "$project_dir" --dirsfirst
```

Here's what each part of the script does:

- `%%bash`: This is a cell magic command in Jupyter notebooks that allows you to run Bash commands directly within a code cell. When you include `%%bash` at the top of a cell in Jupyter, it tells the notebook to interpret the entire cell as Bash commands rather than Python code.
- `project_dir="Project Directory Structure"`: This line defines a variable named `project_dir` and assigns it the value “Project Directory Structure”. This variable will be used to specify the name of the main project directory.
- `mkdir -p “$project_dir”`: This command creates the main project directory specified by the `project_dir` variable. The `-p` option ensures that the command creates intermediate directories as needed, and it won’t throw an error if the directory already exists.
- `mkdir -p “$project_dir/data”`: Creates a subdirectory named “data” inside the main project directory.
- `touch “$project_dir/data/TSLA_stock.csv”`: Creates an empty file named “TSLA_stock.csv” inside the “data” subdirectory. In a real-world scenario, rather than creating an empty file locally, you would typically upload an existing CSV file to an Amazon S3 bucket. Once the file is stored in S3, you can easily copy it to the local directory on your EC2 instance using commands like `aws s3 cp`.
- Similar `mkdir` and `touch` commands are used to create directories and files within the project directory for different purposes, such as source code (`src`), output (`output`), and their respective subdirectories.
- `tree “$project_dir” --dirfirst`: This command generates a visual representation of the project directory structure using the `tree` command. The `--dirfirst` option ensures that directories are listed before files in the output.

**Note** The tree command is not pre-installed on all systems, such as Amazon Linux or Ubuntu on Mac, which we have used for this project. To install the tree command on Ubuntu, we used the following command: `sudo apt-get install tree`; for Amazon Linux: `sudo yum install tree`.

The output of the Bash code, using the tree command, displays the directory structure of `project_dir` and its subdirectories, showing the created files and folders, as illustrated in Figure 2-1 (saved as an image from JupyterLab notebook).

```text
Project Directory Structure
|-- data
|   `-- TSLA_stock.csv
|-- logs
|-- output
|   |-- TSLA_stock.parquet
|   |   `-- _SUCCESS
|   |   `-- part-00000-2c717885-1e92-4091-b73e-c07fb2f42ba8-c000.snappy.parquet
|   `-- TSLA_stock_train.parquet
|       |-- _SUCCESS
|       `-- part-00000-3931d223-097a-4b7f-a6df-6ddc8abfcb5c-c000.snappy.parquet
|-- src
|   |-- pyspark_code
|   |   `-- data_preprocessing.py
|   |-- pytorch_code
|   |   |-- model.py
|   |   `-- model_training.py
|   `-- main.py
|-- tests
|   `-- test.py
|-- visualizations
|   `-- plot.png
|-- README.md
|-- config.yaml
`-- requirements.txt
```

**Figure 2-1.** *Project Directory Structure for Predicting Tesla Stock Price*

CHAPTER 2     SETTING UP A DEEP LEARNING ENVIRONMENT ON AWS

## Creating a Virtual Environment

In addition to establishing a well-defined project structure, it’s advisable to create a virtual environment (e.g., myenv) for managing dependencies and ensuring reproducibility across various environments. This practice isolates the project’s dependencies from other Python projects on the system, thereby preventing conflicts and ensuring consistent execution regardless of the system’s configuration. Once your EC2 instance is up and running, follow the steps below to create, activate, and deactivate a virtual environment on an Ubuntu operating system:

Step 1: Navigate to your home directory:

```bash
cd /home/ubuntu
```

Step 2: Create a virtual environment:

```bash
python3 -m venv myenv
```

This command assumes that Python 3 is installed on your system. Some systems might still default to Python 2.7, which is not compatible with the venv module. You can check your Python version by running

```bash
python3 -version
```

If Python 3 is not installed, you can install it, e.g., using the following commands on Ubuntu:

```bash
sudo apt-get update
sudo apt-get install python3
```

On Amazon Linux:

```bash
sudo yum update
sudo yum install python3
```
