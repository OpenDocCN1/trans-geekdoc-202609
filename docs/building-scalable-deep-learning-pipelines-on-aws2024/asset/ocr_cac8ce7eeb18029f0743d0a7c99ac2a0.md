Step 2: Generate Jupyter Notebook configuration:

+   - Run the code below to generate the Jupyter Notebook
configuration file:

```
[In]: jupyter notebook --generate-config
```

Generating the Jupyter Notebook configuration file allows you to customize various aspects of your Jupyter Notebook environment, such as specifying default settings, configuring security options, and setting up authentication mechanisms.

Step 3: Set password for JupyterLab:

```
[In]: jupyter notebook password
```

Step 4: Start JupyterLab:

+   - Run the following command to start JupyterLab on port
8888 and listen on all available IP addresses:

```
[In]: jupyter lab --ip=0.0.0.0 --port=8888 --no-browser
```

Step 5: Configure security group and access JupyterLab:

+   - Update Security Group: Ensure that your EC2 instance’s security group allows inbound traffic on port 8888.
To do this
- Go to the EC2 Dashboard in the AWS Management
Console.
- In the left-hand menu, under Network & Security,
select Security Groups.
- Choose the security group associated with your
EC2 instance.