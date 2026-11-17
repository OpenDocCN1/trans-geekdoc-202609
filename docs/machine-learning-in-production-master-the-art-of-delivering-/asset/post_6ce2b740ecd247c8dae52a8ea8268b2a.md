

The following figure shows that the IAM user is created:

## Add user

![](img/cc4299656808e62a294f1843a1e18e72_354_0.png)

Figure 13.1: AWS IAM user

The Secret access key is available only when it is created, so you need to download and save it. If lost, then you have to create another one.

Creating access keys for the AWS account root user is not recommended unless required. Rather, create one or more IAM users with the required permissions to execute the tasks.

## Step 3: Install and configure AWS CLI on the local machine

AWS Command-Line Interface (CLI) is a tool that allows the management of several AWS services. It is an open-source tool that enables you to interact with AWS services through commands. First, download and install it, then configure it with AWS credentials. To get started with AWS CLI, follow this link https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html.

For Linux, download the installation file using the curl command, where the -o option specifies the filename that the downloaded package is written to:

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

Unzip the installer as follows:

```
unzip awscliv2.zip
```

The installation command uses a file name install from unzipped aws directory:

```
sudo ./aws/install
```

Verify the installation by checking the version of AWS CLI using the following command:

```
aws --version
```

Restart the terminal if the aws command cannot be found.

Next, configure the AWS CLI with AWS IAM credentials, as shown in the following figure:

```
aws configure
AWS Access Key ID [None]: AKI
AWS Secret Access Key [None]: CPDHawC5
Default region name [None]: us-west-2
Default output format [None]:
```

Figure 13.2: AWS CLI configuration

## AWS CodeCommit

In this case, the Git repository, that is, AWS CodeCommit, is used; however, other remote Git repositories like GitHub can be used. AWS CodeCommit is a private Git repository hosted on AWS. It allows you to create multiple Git repositories and supports a standard set of Git commands, such as push, pull, clone, and log. AWS CodeCommit can be added to a local Git repository as a remote. It allows collaboration and provides security; however, it is a standard practice not to store any personal or sensitive data in it. The good part is that AWS CodeCommit is available to both new and existing users for free up to a certain limit. It does not expire even after 12 months of free tier usage. It is free for the first 5 active users, which includes 1,000 repositories per account, 50 GB of storage per month, and 10,000 Git requests per month.

Go to CodeCommit from Services:

| Services | All Services | Developer Tools | CodeCommit |
|---|---|---|---|

Create a new repository in CodeCommit and then provide the repository name; the description is optional. Repository names are included in the URL of that repository.

Once the repository is created, specific permissions need to be provided; then, create Git credentials to access the CodeCommit repository from the local machine. Go to the IAM console, select Users from the navigation pane and choose the user for which CodeCommit is to be configured. Then, attach the AWSCodeCommitPowerUser policy from the policies list and complete the process. In this case, the IAM user has admin privileges, so there is no need to attach the above-mentioned policy to the IAM user.

Choose the same IAM user and locate HTTPS Git credentials for AWS CodeCommit. Next, select that user and click on the Generate credentials button. It will populate Git credentials, that is, username and password. Password can be seen and downloaded, save it for future use. This password cannot be recovered later on; however, it can be regenerated.

![](img/cc4299656808e62a294f1843a1e18e72_356_0.png)

Figure 13.3: CodeCommit–Git credentials

After creating the CodeCommit repository, clone it to the local machine. Copy project code files into the directory on the local machine. Re-initialize the Git repository using the git init command. Finally, commit and push changes to the CodeCommit repository from the local machine.

Let's consider the scenario of loan prediction where the problem statement is to predict whether a customer’s loan will be approved. Feel free to implement hyperparameter tuning and tweak the model.

First, create an installable package of ML code, and then build a web app using FastAPI; then, create the tests and dependencies file. After that, create Dockerfile and docker-compose.yml files. Finally, create the configuration file buildspec.yml for AWS deployment.

> Note: For code files, refer to the previous chapters. You should create buildspec.yaml file and update the tox.ini file for the current scenario. You need to update src\tests\test_predict.py, src\prediction_model\predict.py, and start.sh for continuous training.

You access the code repository at https://github.com/suhas-ds/AWS-CICD

The following directory structure shows the code files for a CI/CD pipeline:

```
.
|-- src
    |-- prediction_model
        |-- config
            |-- __init__.py
            |-- config.py
        |-- datasets
            |-- __init__.py
            |-- test.csv
            |-- train.csv
        |-- processing
            |-- __init__.py
            |-- data_management.py
            |-- preprocessors.py
        |-- trained_models
            |-- __init__.py
            |-- classification_v1.pkl
        |-- VERSION
        |-- __init__.py
        |-- pipeline.py
        |-- predict.py
        |-- train_pipeline.py
|-- tests
    |-- pytest.ini
    |-- test_predict.py
|-- MANIFEST.in
|-- README.md
|-- requirements.txt
|-- setup.py
|-- tox.ini
|-- .gitignore
|-- Dockerfile
```

```
|__ README.md
|__ buildspec.yaml
|__ docker-compose.yml
|__ main.py
|-- pytest.ini
|-- requirements.txt
|-- runtime.txt
|-- start.sh
|-- test.py
└── tox.ini
```

## tox.ini

The tox is a free and open-source tool used for testing Python packages or applications. It creates the virtual environment and installs the required dependencies in it; finally, it runs the tests for that Python package. You need to update the tox.ini file as shown in the following code.

```
1. [tox]
2. envlist = my_env
3. skipsdist=True
4.
5. [testenv]
6. install_command = pip install {opts} {packages}
7. deps =
8.   -r requirements.txt
9.
10. setenv =
11.   PYTHONPATH=src/
12.
13. commands=
14.   pip install requests
15.   pytest -v src/tests/ --junitxml=pytest_reports/Prediction_test_report.xml
16.   pytest -v test.py --junitxml=pytest_reports/API_test_report.xml
```

The **skipsdist=True** flag indicates not to perform a packaging operation. It means the package will not be installed in a virtual environment before performing any test. Set **PYTHONPATH** to the **src/** directory where Python package files are placed. In the commands section, pytest commands will be executed, and the results of the tests will be exported in `.xml` files in the **pytest_reports** directory.

### .\src\prediction_model\predict.py

Here, add the **train_accuracy** function to the _predict.py_ file that will return the accuracy score.

```
1. def train_accuracy(input_data):
2.     """ Checking accuracy score of training data """
3.
4.     # Read Data
5.     data = pd.DataFrame(input_data)
6.     y_train = np.where(data['Loan_Status']=='Y', 1, 0).tolist()
7.
8.     # Prediction
9.     prediction = _loan_pipe.predict(data[config.FEATURES])
10.    y_pred = prediction.tolist()
11.    score = accuracy_score(y_train,y_pred)*100
12.    return score
```

### .\src\tests\test_predict.py

Now, add the **test_score** function to the _test_predict.py_ file that will test whether the training accuracy score is between 70 to 95. You can change this range.

```
1. from prediction_model.predict import train_accuracy
2.
3. def test_score():
4.     """ This function will check the accuracy score of training data
...
5.     data = load_dataset(file_name=config.TRAIN_FILE)
6.     score = train_accuracy(data)
7.     assert 70 <= score <= 95
```

After a successful push from the local terminal, code files will be displayed in the cloud source repository.

