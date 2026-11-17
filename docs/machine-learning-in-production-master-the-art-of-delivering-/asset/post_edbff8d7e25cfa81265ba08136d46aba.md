
To start a Flask application, you need to use the **run()** function. If you set **debug=True** inside the **run()** function, then it becomes easy to track the error. When you enable debug mode, the server will restart every time you make changes in the app file and save it. If an error occurs, then it shows the reason in the browser itself. However, you should not use this feature while deploying models in the production environment.

In a Flask, you can call static files like CSS or JavaScript files to render the web page of the app. The **route()** function guides the Flask to the URL called by the function.

```
pip install Flask
```

To run the Flask application in the terminal, go to the directory where *app.py* and other required files are located:

```
python app.py
```

Create an *index.html* file with the following HTML code to build the front end for the users. This will enable the users to provide the input data through UI.

```
<html>
<head>
<title>LOAN PREDICTION</title>
</head>
<body>
<h2 align="center">LOAN PREDICTION</h2>
<br/>
<form action="/predict" method="POST">
<table align="center" cellpadding = "10">
<!----- First Name ------------------------------->
<tr>
<td>FIRST NAME</td>
<td>
<input type="text" name="First_Name" maxlength="30"
placeholder="characters a-z A-Z"/>
</td>
</tr>
<!----- Last Name ------------------------------->
<tr>
<td>LAST NAME</td>
<td>
    <input type="text" name="Last_Name" maxlength="30"
placeholder="characters a-z A-Z" />
</td>
</tr>
<!---- Gender -------------------------------------------------------->
<tr>
<td>GENDER</td>
<td>
    <input type="radio" name="gender" id="gender"
    value="1">Male</input>
</td>
</tr>
<!---- Marital Status -------------------------------------------------------->
<tr>
<td>MARRIED</td>
<td>
    <input type="radio" name="married" id="married" value="1">
Yes </input>
</td>
</tr>
<!------ Income ---------------------------------------------------------------->
<tr>
<td>TOTAL INCOME</td>
<td>
    <input type="text" name="total_income" maxlength="30"
    placeholder="$(thousands)" />
</td>
</tr>
<!----- Loan Amount ------->
<tr>
<td>LOAN AMOUNT</td>
<td>
    <input type="text" name="loan_amt" maxlength="30"
    placeholder="$(thousands)" />
</td>
</tr>
<!----- Credit History ------->
<tr>
<td>CREDIT HISTORY</td>
<td>
    <input type="radio" name="credit_history" id="credit_history"
    value="1"> Yes </input>
    <input type="radio" name="credit_history" id="credit_history"
    value="0"> No </input>
</td>
</tr>
<!----- Submit and Reset ------->
<tr>
    <td colspan="2" align="center">
        <input type="submit" value="Submit">
        &nbsp;&nbsp; <!---- to add extra space ---->
        <input type="reset" value="Reset" onclick="location.href='/';">
    </td>
</tr>
</table>
</form>
<h3 align="center"> {{ prediction }} </h3>
</body>
</html>
```

Here, the result.html file will display the prediction output to the users:

```
<!doctype html>
<html>
<body>
<h1>{{ prediction }}</h1>
</body>
</html>
```

Now, create an app.py file for the Flask application:

```
# Importing Dependencies
from flask import Flask,render_template,url_for,request
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
import numpy as np
import pickle
import os
```

The next step is to load the serialized model object to make the prediction:

```
app = Flask(__name__)
port = int(os.environ.get("PORT", 80))
# Loading the trained model
pickle_in = open('trained_model/model_rf.pkl', 'rb')
model = pickle.load(pickle_in)
```

Now, create the views for the Flask application. The following code will render the HTML template, which will be the landing page of the Flask application. app.route('/') will route to the home page URL; the trailing slash '/' is generally used as a convention for the home page.

```
# Views
@app.route('/')
def home():
    return render_template('index.html')
```

Now, create a view for the predict() function. app.route('/predict') will route to the home page URL. The POST method type allows you to send data to a server to update or create a target resource.

```
@app.route('/predict', methods=['POST'])
def predict():
    if request.method == 'POST':
        # Fetch Value for Gender
        gender = request.form['gender']
        if gender == "Female":
            gender = int(0.0)
        if gender == "Male":
            gender = int(1.0)

        # Fetch Value for Married
        married = request.form['married']
        if married == "No":
            married = int(0.0)
        if married == "Yes":
            married = int(1.0)

        # Fetch value for LoanAmount
        loan_amt = float(request.form['loan_amt'])

        # Fetch value for Total_Income
        total_income = float(request.form['total_income'])

        # Fetch value for Prior Credit_Score
        credit_history = request.form['credit_history']
        if credit_history == "No":
            credit_history = int(0.0)
        if credit_history == "Yes":
            credit_history = int(1.0)

        to_predict_list = [gender, married, total_income, loan_amt, credit_history]
        prediction_array = np.array(to_predict_list, dtype=np.float32).reshape(1, 5)

        # Making Predictions using the trained model
        prediction = model.predict(prediction_array)
        prediction_value = prediction[0]

        if int(prediction_value) == 1:
            status="Congratulations! your loan approval request is processed"
        if int(prediction_value) == 0:
            status="Sorry! your loan approval request is rejected"

        return render_template('index.html',prediction = status)
```

Add error handling functionality, as follows:

```
@app.errorhandler(500)
def internal_error(error):
    return "500: Something went wrong"

@app.errorhandler(404)
def not_found(error):
    return "404: Page not found",404
```

Finally, you will define the main function as shown below:

```
if __name__ == '__main__':
    app.run(host='0.0.0.0', port=port)
```

## Gunicorn

The Gunicorn is an application server for running a Python app. Gunicorn is WSGI compatible, so it can communicate with multiple WSGI applications. In the current case, Gunicorn translates the request received from Nginx for the Flask app and vice versa.

To install Gunicorn, execute the following command:

```
sudo apt-get install gunicorn3
```

Go to the directory where the app.py file is located and run:

```
gunicorn3 app:app
```

This command helps to know which IP and port are being used by Gunicorn. In this case, it is 8000 and IP can be 0.0.0.0 or 127.0.0.1.

## NGINX

NGINX is a high-performance, highly scalable open-source, and reverse proxy web server. It can perform load balancing and caching application instances. It accepts incoming connections and decides where they should go next. In the current case, it sits on top of a Gunicorn.

To install NGINX, execute the following command:

```
sudo apt-get install nginx
```

You can check the status of NGINX using the following command:

```
sudo service nginx status
```

Now, go to the following path:

```
cd /etc/nginx/sites-enabled/
```

> Note: NGINX configuration files do not have any extension, and every line should be closed using ; (semicolons).

Create a new configuration file for the Flask app:

```
sudo nano flask_app
```

Then, add the following snippet and save the file:

```
server{
    listen 80;
    server_name 0.0.0.0;

    location / {
        proxy_pass http://unix:/home/suhas/webapi/flask/flaskapp.sock;
    }
}
```

Here, you are dictating NGINX to listen to port **80**. Inside the location block, pass the request to the socket using **proxy_pass**. After changing the NGINX file, restart the NGINX service using the following command:

```
sudo service nginx restart or sudo systemctl restart nginx
```

You can check the status of NGINX using the following command:

```
sudo service nginx status
```

Go to the directory where the _app.py_ file is located and run the following command to start the Gunicorn server:

```
gunicorn3 app:app
```

Open a new tab in the browser and enter the IP in the address bar. You should see the Flask app up and running.
