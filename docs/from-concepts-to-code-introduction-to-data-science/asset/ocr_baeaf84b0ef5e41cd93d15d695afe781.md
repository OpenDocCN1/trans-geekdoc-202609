We can test the script by opening a terminal, navigating to the directory with the script, and running the command:

```
python housing_script.py
```

The output contains the R-squared as expected:

R-squared: 0.6092160009090456

For this simple model, the only module in use is scikit-learn. We include it in the requirements.txt file with its corresponding version:

```
scikit-learn==1.0.2
```

Next, we create the Dockerfile to set up the Python environment for running the script. Note the file name does not have an extension. The Dockerfile uses specific commands, which are explained below.

```
FROM python:3.9
WORKDIR /src
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY .
CMD ["python","housing_script.py"]
```

+   - Line 1 specifies that Python 3.9 is the base image.
- Line 2 sets the working directory to /src.
- Line 3 copies the requirements.txt file to the working directory.
- Line 4 installs the Python packages in requirements.txt using pip.
- Line 5 copies the files in the current directory to the working directory.
- Line 6 runs the file housing.script.py using Python.

Lastly, we will build the Docker image. We can first verify that Docker is running by opening a terminal and running this command:

```
docker info
```

If Docker is not running, an error like this might appear in the output:

```
Server:
ERROR: error during connecting: this error may indicate that the docker daemon is not running...
```

Once we verify that Docker is running, we can navigate to the directory with the Dockerfile and run this command:

```
docker build -t housing
```