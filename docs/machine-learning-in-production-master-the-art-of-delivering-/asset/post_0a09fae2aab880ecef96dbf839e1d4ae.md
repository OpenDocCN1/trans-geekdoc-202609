
14. self.lbl5.place(x=100, y=250)
15. self.t5.place(x=200, y=250, width=165)
17. self.b1=Button(win, text='Predict', command=self.predict, fg='blue')
18. self.b1.place(x=170, y=300)
20. self.lbl6.place(x=100, y=350)
21. self.t6.place(x=200, y=350)

Finally, define the **predict()** to make the prediction using the ML model based on user inputs.

```
1. # For making predictions
2. def predict(self):
3. self.t6.delete(0, 'end')
4. gender = float(self.t1.get())
5. married = float(self.t2.get())
6. income = float(self.t3.get())
7. loan_amt = float(self.t4.get())
8. credit_hist = float(self.t5.get())
9. prediction = model.predict([[gender, married, income, loan_amt, credit_hist]])[0]
10. if prediction == 0:
11. pred = 'Rejected'
12. else:
13. pred = 'Approved'
15. self.t6.insert(END, str(pred))
```

The class declaration is done here.

Use the Tk class to create the main window and call the mainloop() to keep the window displayed.

Also, the application window does not appear on the screen till mainloop() is not called, as it takes all the objects and widgets and renders them on screen.

```
1. window=Tk()
2.
3. mywin=MyWindow(window)
4.
5. # Create a title
6. window.title('ML App')
7.
8. # Define the size of the window
9. window.geometry("400x400+10+10")
10.
11. window.mainloop() #Keep the window displaying
```

Create a ml_app.py file for the Tkinter app and run it. It should make predictions based on the given input.

## Convert Python app into Windows EXE file

Now, you can convert this Tkinter - ML app to Windows executable application using Pyinstaller, with the following steps. Pyinstaller packages a Python application and its dependencies into a single package that can be run independently without installing a Python interpreter.

Let’s create a virtual environment and install all the required dependencies.

Here, a virtual environment is created with Python version 3.7 using conda, as follows:

```
conda create -n envv_tkinter python=3.7 -y
```

Once it is created, activate it using:

```
source activate envv_tkinter
```

> Note: To remove the conda environment, you can execute the following command conda env remove -n envv_tkinter:

```
pyinstaller --noconfirm --onefile --windowed --icon "E:/tkinter_ml_app/python_104451.ico" --add-data "E:/tkinter_ml_app/trained_model/model.pkl;." --hidden-import "sklearn" --hidden-import "sklearn.ensemble._forest" --hidden-import "sklearn.neighbors._typedefs" --hidden-import "sklearn.utils._weight_vector" --hidden-import "sklearn.neighbors._quad_tree" "E:/tkinter_ml_app/ml_app.py"
```

The preceding command will convert the Python-based Tkinter app to a Windows executable file that can be used for prediction.

Where:

- -y, --noconfirm: Will replace output directory without asking for confirmation
- -F, --onefile: Will create one file bundle executable
- -D, --onedir: Will create one folder bundle containing the Windows executable file
- --add-data: Additional non-binary files or folders to be added to the executable
- -c, --console, --nowindowed: Opens a console window for standard I / O (default)
- -w, --windowed, --noconsole: Used to not provide a console window for standard I / O
- --hidden-import MODULENAME: Used to name an import not visible in the code of the script(s); this option can be used multiple times

For more details, refer to:
https://pyinstaller.org/en/stable/usage.html

The following figure shows the status message after executing the preceding command. It states the EXE file creation success message.

![](img/cc4299656808e62a294f1843a1e18e72_192_0.png)

Figure 8.3: Converting Python app to Windows app

Now, open the ml_app.exe file located in the dist folder.

The following figure shows the files and folders of the ML-based Tkinter app:

```
__pycache__
build
data
dist
trained_model
ml_app
ml_app.spec
python_104451
Readme
requirements
train
```

Figure 8.4: Tkinter ML app

Open the app; you should see the window of the Tkinter app. It should display the prediction based on user input.

The following figure displays the prediction based on user data provided:

![](img/cc4299656808e62a294f1843a1e18e72_193_0.png)

Figure 8.5: Tkinter ML app

## Build an ML-based app using kivy and kivyMD

In this section, using the pickle object of the trained model generated earlier in this chapter, let's develop and deploy the FastAPI endpoint on the remote server, i.e., Heroku. You will learn how to deploy ML models on the Heroku platform with CI / CD pipeline in the upcoming chapter.

Moreover, you can deploy this FastAPI app using any other hosting service, such as PythonAnywhere or Amazon EC2. In the current scenario, a remote endpoint is used to make predictions in the Kivy app.

So, whenever users pass the data in the kivy app and press the **Predict** button, it will send the parameters to the API endpoint, where it will pass the received parameters to the model object and in return, send the prediction to API. The Kivy app will fetch the output (prediction) provided by the API.

Let's install FastAPI and uvicorn (an **ASGI (Asynchronous Server Gateway Interface)** server for production) as shown below:

```
pip install fastapi uvicorn
```

Note: FastAPI requires Python 3.6+

Now, create an `app.py` file. First, load the dependencies and pickle the object of the trained model. Also, create a FastAPI instance and assign it to the app. So, the app will be the point of interaction while creating API.

```
1. # Import dependencies
2. from fastapi import FastAPI
3. from pydantic import BaseModel
4. import uvicorn
5. import pickle
6. from fastapi.middleware.cors import CORSMiddleware
7.
8. app = FastAPI()
9.
10.origins = ["*"]
11.
```

```
12. app.add_middleware(
13.     CORSMiddleware,
14.     allow_origins=origins,
15.     allow_credentials=True,
16.     allow_methods=["*"],
17.     allow_headers=["*"],)
18.
19. # Load the trained model
20. trained_model = 'trained_model/model_rf.pkl'
21. # pickle_in = open(trained_model, 'rb')
22. model = pickle.load(open(trained_model, 'rb'))
```

Define the class **LoanPred**, which defines the datatype expected from the client.

The **LoanPred** class is used for the data model that is inherited from **BaseModel**. Add a root view of the function that returns **'message': 'Loan Prediction App'** for the home page.

```
1. class LoanPred(BaseModel):
2.     Gender: float
3.     Married: float
4.     ApplicantIncome: float
5.     LoanAmount: float
6.     Credit_History: float
7.
8. @app.get('/')
9. def index():
10.     return {'message': 'Loan Prediction App'}
```

The following function will create a UI for user input. Here, create a **/predict** as an endpoint, also known as the route. Then, add the parameter of the type data model created, which is **LoanPred**.

```
1. # Defining the function which will make the prediction using the data which the user inputs
2. @app.post('/predict_status')
3. def predict_loan_status(loan_details: LoanPred):
4.     data = loan_details.dict()
5.     gender = data['Gender']
6.     married = data['Married']
7.     income = data['ApplicantIncome']
8.     loan_amt = data['LoanAmount']
9.     credit_hist = data['Credit_History']
10.
11.     # Making predictions
12.     prediction=model.predict([[[gender, married, income, loan_amt, credit_hist]]])
13.
14.     if prediction == 0:
15.         pred = 'Rejected'
16.     else:
17.         pred = 'Approved'
18.
19.     return {'status':pred}
20.
21. @app.get('/predict')
22. def get_loan_details(gender: float, married: float, income: float,
23.                     loan_amt: float, credit_hist: float):
24.     prediction = model.predict([[[gender, married, income, loan_amt, credit_hist]]]).tolist()[0]
25.     print(prediction)
26.     if prediction == 0:
27.         pred = 'Rejected'
28.     else:
```

```
29. pred = 'Approved'
30.
31. return {'status':pred}
32.
33. if __name__ == '__main__':
34. uvicorn.run(app, host='0.0.0.0', port=4000)
```

Now, it’s time to run the app and see standard UI auto-generated by FastAPI, which uses swagger, now known as openAPI.

```
uvicorn app:app --reload
```

The preceding command can be interpreted as follows:

- The app refers to the name of the file in which the API is created.
- The app is the instance defined in it or a file.
- --reload will simply restart the FastAPI server every time changes are made in the app file.

## KivyMD app

Kivy is an open-source software library for the quick development of apps with a simple GUI. Kivy is written in Python, so in order to use it, you should have Python installed on your system. Unlike Tkinter, it is not pre-installed with Python; you need to install it separately.

KivyMD is an extension of the kivy framework. It is a collection of Material Design (MD) widgets and is mainly used for GUI building along with kivy. It is a good idea to create a virtual environment first, as it helps maintain different packages easily. You can install kivy and KivyMD using the following commands:

```
pip install kivy
pip install kivymd
```

Use the deployed endpoint on the remote server. Keep it simple for now. Import the required dependencies first. Here, import MDApp, which is a base app. Build the app on top of this base app as it takes care of initialization and booting up the app.

Then, import the Builder function for the front end of the app.

Now create a file named main.py and add the following code to it. First, import the required dependencies into it.
