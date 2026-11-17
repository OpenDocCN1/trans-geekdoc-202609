Define the class **LoanPred**, which defines the data type expected from the client.

You can use the `LoanPred` class for the data model that is inherited from `BaseModel`. Then, add a root view of the function that returns 'message': 'Loan Prediction App' for the home page.

```
1. class LoanPred(BaseModel):
2.     Gender: str
3.     Married: str
4.     Dependents: str
5.     Education: str
6.     Self_Employed: str
7.     ApplicantIncome: float
8.     CoapplicantIncome: float
9.     LoanAmount: float
10.    Loan_Amount_Term: float
11.    Credit_History: float
12.    Property_Area: str
13.
14. @app.get('/')
15. def index():
16.     return {'message': 'Loan Prediction App'}
```

Here, create `/predict_status` as an endpoint, also known as the route. Then, add `predict_loan_status()` with a parameter of the type data model that you created as `LoanPred`.

```
1.    #Defining the function which will make the prediction using the data
    which the user inputs
2. @app.post('/predict_status')
3. def predict_loan_status(loan_details: LoanPred):
4. data = loan_details.dict()
5. Gender = data['Gender']
6. Married = data['Married']
7. Dependents = data['Dependents']
```