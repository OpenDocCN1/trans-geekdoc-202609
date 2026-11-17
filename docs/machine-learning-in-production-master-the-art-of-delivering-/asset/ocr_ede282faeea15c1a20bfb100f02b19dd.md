that converts the Python code into interactive apps and enables data scientists to build data and model-based apps quickly.

Let's install streamlit using the following command:

```
pip install streamlit
```

Verify the streamlit installation using the following:

```
streamlit hello
```

Now, create a streamlit_app.py file for the ML-based streamlit application:

```
1. import pickle

2. import streamlit as st

3.

4. # Loading the trained model

5. trained_model = 'trained_model/model_rf.pkl'

6. model = pickle.load(open(trained_model, 'rb'))

7.

8. @st.cache()
```

The following function will make the prediction based on input received from the front end:

```
1. # The following function will make the prediction based on data
   provided by the user

2. def prediction(Gender, Married, ApplicantIncome, LoanAmount,
   Credit_History):

3.   # Pre-processing user input

4.   if Gender == "Male":

5.     Gender = 1

6.   else:

7.     Gender = 0

8.

9.   if Married == "Unmarried":

10.    Married = 1

11.  else:
```