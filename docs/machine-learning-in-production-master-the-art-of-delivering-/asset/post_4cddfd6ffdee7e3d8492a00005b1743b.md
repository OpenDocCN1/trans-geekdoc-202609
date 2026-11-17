
def index():
    return {'message': 'Loan Prediction App'}

@app.get('/health')
def healthcheck():
    return {'status':'ok'}

Here, create **/predict_status** as an endpoint, also known as a route. Then, add **predict_loan_status()** with a parameter of the type data model, that is, **LoanPred**.

```python
# Defining the function which will make the prediction using the data
# which the user inputs
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

The following function will create the UI for user input. Here, create /predict as an endpoint, also known as a route, and declare input data types expected from users.

```python
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
    pass
```

The file for FastAPI is completed.

## requirements.txt

Now, create the requirements.txt file, as follows. In this file, you can define the model requirements, test requirements, and FastAPI requirements separately for better understanding and ease of management.

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

Dockerfile contains a list of commands or instructions to be executed while building the Docker image. Docker uses this file to build the Docker image.

```
FROM python:3.7-slim-buster

COPY ./start.sh /start.sh

RUN chmod +x /start.sh

ENV PYTHONPATH "${PYTHONPATH}:/app/src/"

COPY . /app

RUN chmod +x /app

RUN pip install --no-cache-dir --upgrade -r app/requirements.txt

CMD ["./start.sh"]
```

## docker-compose.yml

The web service builds from the Dockerfile in the current directory and mounts the app directory on the host to /app inside the container.

```
version: "3.9" # optional since v1.27.0
services:
web:
build: .
volumes:
- ./app:/app
```

## pytest.ini

Pytest allows you to use a global configuration file, that is, *pytest.ini*, where you can keep the settings and additional arguments that are to be passed whenever you run the command. Add **-p no:warnings** to the **addopts** option, which will suppress the warnings. This section will execute the parameters when pytest runs.

```
[pytest]

addopts = -p no:warnings
```

## runtime.txt

Declare the Python version to be used in this file.

```
python-3.7
```

## start.sh

This is a shell script that contains a series of commands to be executed by the bash shell. The first line of this file tells which interpreter should be used to execute this script.

It will install the **prediction_model** package from `src/` placed in the `app/` folder and run the FastAPI app in the next command. Here, it will get the PORT from the Heroku environment, so you do not need to declare it explicitly. Heroku will run the app on any available port. The **main** is the file name located in the `app` directory, followed by `:app`, which is a FastAPI object to be called.

```
#!/bin/sh

pip install app/src/

uvicorn app.main:app --host 0.0.0.0 --port $PORT
```

Make sure you remove the **--reload** option if you are using it. The **--reload** option consumes much more resources; moreover, it is unstable. You can use it during development but should not use it in production.

## test.py

This file will enable you to test the FastAPI app using **TestClient**. FastAPI provides the same **starlette.testclient** as **fastapi.testclient**; however, it comes directly from Starlette. With this, you can check the app’s routes without running the app explicitly.

This file will test the root path of the app and sample prediction by passing the data.

```
# Importing dependencies

from main import app

from fastapi.testclient import TestClient

import pytest
import requests
import json
```

Create a TestClient() by passing a FastAPI application to it as an argument:

```
client = TestClient(app)
```

Define the functions with a name starting with test_ as per standard pytest conventions:

```
def test_read_main():
    response = client.get("/")
    assert response.status_code == 200
    assert response.json() == {'message': 'Loan Prediction App'}
```

Write simple assert statements to check the output:

```
def test_pred():
    data = {
        "Gender": "Male",
        "Married": "Yes",
        "Dependents": "0",
        "Education": "Graduate",
        "Self_Employed": "No",
        "ApplicantIncome":5720,
        "CoapplicantIncome":0,
        "LoanAmount":110,
        "Loan_Amount_Term":360,
        "Credit_History":1,
        "Property_Area": "Urban"
    }

    response = client.post("/predict_status", json=data)
    assert response.json()["status"] != ""
    assert response.json() == {"status": "Approved"}
```

## tox.ini

This is the tox configuration file. Tox automates and standardizes the testing in Python. It is a virtualenv management and test command-line tool to check if your package is compatible with different Python versions. Tox will first create a virtual environment based on the configuration provided, install dependencies and finally execute the commands provided in the configuration.

**tox-gh-actions** is a plugin that enables tox to run on GitHub Actions. Hence, you need to install **tox-gh-actions** in the GitHub Actions workflow before running the tox command.

This file aims to check the functioning of the package against Python-3.7. It will install the required dependencies and run the pytest command.

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

## workflow.yml
