+   - Click the Inbound rules tab and then Edit inbound rules.
- Add a rule that allows Custom TCP traffic on port 8888 from your IP or from any IP (0.0.0.0/0) for testing purposes (use caution with this option for security reasons).
  - Access JupyterLab: Open a web browser and navigate to http://<your_ec2_instance_ip>:8888.

You should now be able to access Jupyter your EC2 instance using the password you generated.

# ## Setting Up a Databricks Account and Workspace

If you prefer to use Databricks for preprocessing your data, the steps below provide an overview of creating a Databricks account, setting up a workspace, and connecting it with your AWS account:

Step 1: Sign up for Databricks.

+   - Go to the Databricks website at https://www.databricks.com/.
- Click the “Try Databricks” button at the top-right corner.
- Fill in the required information to create your account, including your first and last name, email address, company, title, and country, and pick your cloud provider (in this case, AWS; the others being Microsoft Azure and Google Cloud Platform).