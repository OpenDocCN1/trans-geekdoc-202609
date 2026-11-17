
@app.get('/health')
def healthcheck():
    return {'status':'ok'}

Here, create `/predict_status` as an endpoint, also known as the route. Then, add `predict_loan_status()` with a parameter of the type data model, that is, `LoanPred`.

```
# Defining the function which will make the prediction using the data which the user inputs
@app.post('/predict_status')
def predict_loan_status(loan_details: LoanPred):
    data = loan_details.dict()
    Gender = data['Gender']
    Married = data['Married']
    Dependents = data['Dependents']
    Education = data['Education']
    Self_Employed = data['Self_Employed']
    ApplicantIncome = data['ApplicantIncome']
    CoapplicantIncome = data['CoapplicantIncome']
    LoanAmount = data['LoanAmount']
    Loan_Amount_Term = data['Loan_Amount_Term']
    Credit_History = data['Credit_History']
    Property_Area = data['Property_Area']

    # Making predictions
    input_data = [Gender, Married, Dependents, Education,
        Self_Employed, ApplicantIncome, CoapplicantIncome,
        LoanAmount, Loan_Amount_Term, Credit_History, Property_Area]
    cols = ['Gender','Married','Dependents',
        'Education','Self_Employed','ApplicantIncome',
        'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
        'Credit_History','Property_Area']
    data_dict = dict(zip(cols,input_data))
    prediction = make_prediction([data_dict])['prediction'][0]

    if prediction == 'Y':
        pred = 'Approved'
    else:
        pred = 'Rejected'

    return {'status':pred}
```

The following function will create the UI for user input. Here, create /predict as an endpoint, also known as a route, and declare the input data types expected from users.

```
@app.post('/predict')
def get_loan_details(Gender: str, Married: str, Dependents: str,
                     Education: str, Self_Employed: str, ApplicantIncome: float,
                     CoapplicantIncome: float, LoanAmount: float, Loan_Amount_Term: float,
                     Credit_History: float, Property_Area: str):

    input_data = [Gender, Married, Dependents, Education,
                  Self_Employed, ApplicantIncome, CoapplicantIncome,
                  LoanAmount, Loan_Amount_Term, Credit_History, Property_Area]
    cols = ['Gender','Married','Dependents',
            'Education','Self_Employed','ApplicantIncome',
            'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
            'Credit_History','Property_Area']

    data_dict = dict(zip(cols,input_data))
    prediction = make_prediction([data_dict])['prediction'][0]
    if prediction == 'Y':
        pred = 'Approved'
    else:
        pred = 'Rejected'

    return {'status':pred}

if __name__ == '__main__':
    uvicorn.run("main:app", host="0.0.0.0", port=port, reload=False)
```

The FastAPI file is completed.

## requirements.txt

Now, let's create a requirements.txt file, as follows. In this file, model requirements, test requirements, and FastAPI requirements are defined separately for better understanding and ease of management.

```
# Model building requirements
joblib==0.16.0
numpy==1.19.0
pandas==1.0.5
scikit-learn==0.23.1
scipy==1.5.1
sklearn==0.0

# testing requirements
pytest<5.0.0,>=4.6.6
requests

# packaging
setuptools==40.6.3
wheel==0.32.3

# FastAPI app requirements
fastapi>=0.68.0,<0.69.0
pydantic>=1.8.0,<2.0.0
uvicorn>=0.15.0,<0.16.0
gunicorn>=20.1.0
```

## Dockerfile

Dockerfile contains a list of commands or instructions to be executed while building the Docker image.

```
FROM python:3.7-slim-buster

COPY ./start.sh /start.sh

RUN chmod +x /start.sh

ENV PYTHONPATH "${PYTHONPATH}:app/src/"

COPY . /app

RUN chmod +x /app

# expose the port that uvicorn will run the app on
ENV PORT=8000
EXPOSE 8000

RUN pip install --no-cache-dir --upgrade -r app/requirements.txt

CMD ["./start.sh"]
```

## docker-compose.yml

This builds the web service from the Dockerfile in the current directory and mounts the app directory on the host to /app inside the container.

```
version: "3.9"  # optional since v1.27.0
services:
  web:
    build: .
    volumes:
      - ./app:/app
```

## pytest.ini

Pytest allows you to use a global configuration file, that is, *pytest.ini*, where you can keep settings and additional arguments that you pass whenever you run the command. You can add **-p no:warnings** to **addopts** field, which will suppress the warnings. This section **will execute** the parameters when pytest runs.

```
[pytest]
addopts = -p no:warnings
```

## runtime.txt

This file is optional. In this file, you can declare the Python version to be used.

```
python-3.7
```

## start.sh

This is a shell script that contains a series of commands to be executed by the bash shell. The first line of this file dictates which interpreter should be used to execute this script.

It will install the **prediction_model** package from **src/** placed in **app/** and run the FastAPI app in the next command. The *main.py* is the file name located in the *app* directory.

```
#!/bin/bash
pip install app/src/
python app/main.py
```

Make sure you remove the **--reload** option if you are using it. The **--reload** option consumes much more resources, and it is also unstable. You can use it during development but should not use it in production.

## test.py

This test file will enable testing the FastAPI app using **testclient**. FastAPI provides the same **starlette.testclient** as **fastapi.testclient**; however, it comes directly from Starlette. With this, you can check the app's routes without running them from the app explicitly.

This file will test the root path of the app and model predictions by passing the data.

```
# Importing dependencies
from main import app
from fastapi.testclient import TestClient
import pytest
import requests
import json
```

Create a **TestClient()** and pass a FastAPI application to it.

```
client = TestClient(app)
```

Define the test functions with a name starting with **test_** as per standard naming conventions of pytest:

```
def test_read_main():
    response = client.get("/")
    assert response.status_code == 200
    assert response.json() == {'message': 'Loan Prediction App'}
```

Write simple assert statements in the test function to check the output.

```
def test_pred():
    data = {
        "Gender":"Male",
        "Married":"Yes",
        "Dependents":"0",
        "Education":"Graduate",
        "Self_Employed":"No",
        "ApplicantIncome":5720,
        "CoapplicantIncome":0,
        "LoanAmount":110,
        "Loan_Amount_Term":360,
        "Credit_History":1,
        "Property_Area":"Urban"
    }

    response = client.post("/predict_status", json=data)
    assert response.json()["status"] != ''
    assert response.json() == {"status": "Approved"}
```

## tox.ini

This is the tox configuration file. The tox automates and standardizes the testing in Python. It is a virtualenv management and test command-line tool to check whether your package is compatible with different Python versions. The tox will first create a virtual environment based on the configuration provided and then install dependencies. Finally, it will execute the commands provided in the configuration.

**tox-gh-actions** is a plugin that enables tox to run on GitHub Actions. Hence, you need to install **tox-gh-actions** in the GitHub Actions workflow before running the tox command.

This file will check the package compatibility with Python-3.7. First, it will install the required dependencies and then run the pytest commands.

```
[tox]
envlist = py37
skipsdist=True

[gh-actions]
python =
  3.7: py37

[testenv]
install_command = pip install {opts} {packages}
deps =
  -r requirements.txt

setenv =
  PYTHONPATH=src/

commands=
  pip install requests
  pytest -v test.py
  pytest -v src/tests/
```

Once all files and codebase are ready, run the app on the local machine. If the app is running on a local machine, then deploy the app to the Azure Container Registry.

Build a Docker image on a local machine using the following command:

```
sudo docker build . -t mlappcd.azurecr.io/mlapp-cd:v1
```

Then, run the Docker image using the following command:

```
sudo docker push mlappcd.azurecr.io/mlapp-cd:v1
```

At this point, you should see an ML app up and running on the local machine.

## Infrastructure setup

First off, set up infrastructure on Azure cloud. In this section, you will learn to set up an Azure Container Registry (ACR) and create a web app container using the Azure App Service.

## Azure Container Registry

To begin with, push the Docker image to the Azure Container Registry from the local machine, and from the next time onward, GitHub Actions will push the image. This Docker image will be pulled by the Azure App Service to run a web app container.
