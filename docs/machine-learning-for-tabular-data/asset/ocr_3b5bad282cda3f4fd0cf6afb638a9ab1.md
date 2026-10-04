```
<form action="{ url_for('home') }">
<input type="submit"
value="Get another prediction"
style="font-size: 20px; width: 40%; height: 30px;"/>
</form>
```

As shown in 10.8, show-prediction.html does not contain any JavaScript functions. The HTML for the page defines the text that appears on the page, and the button Get Another Prediction returns the user to home.html. Figure 10.4 shows how the elements we have discussed in this section appear in show-predicton.html.

![](bbox=[0.109, 0.335, 0.859, 0.613])

Figure 10.4 Key elements in show-prediction.html

Now that we have examined all the components of web deployment, we will review the rationale for deploying our model simply on the web in the next section.

# 10.1.5 Exercising the web deployment

Now that we have gone through the components that make up the web deployment, the next step is to see the deployment in action. To exercise the web deployment,

+   - Create a deployment on your local system and clone the repo https://github.com/lmassaron/ml_on_tabular_data,
- Make chapter_10 your current deployment and start the Flask server module:

```
python flask_endpoint_deploy.py
```