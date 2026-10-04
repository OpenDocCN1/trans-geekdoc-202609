# Public clouds and machine learning operations

3 Once the Flask server is running, go to localhost:5000 in a browser to
exercise the deployment.

Congratulations! You have exercised a deep learning model trained on tabular data
the context of a simple, local web application. This deployment is an efficient way for
us to exercise the trained model and see if it behaves as expected. However, this very
basic deployment does not incorporate many of the characteristics we expect to have
in a production deployment. For example, we don't want the resources for serving the
model to be limited by our local system. In the remainder of this chapter, we will exam-
ine we can use this same web application to exercise the trained model deployed
from an endpoint in a cloud environment.

# 10.2 Public clouds and machine learning operations

The simple deployment that we reviewed in the previous section demonstrates
s useful aspects of what it takes to put a trained model into production, but it has
s serious limitations. It is running entirely on a local system, so it won't be acces-
sible to anyone who doesn't have access to the local system. This is probably a good
thing, because this deployment does not incorporate the characteristics that we want
to have in a production deployment, including

+   - Scaling capacity to meet. What happens if the interest rate drops and the
demand for price predictions doubles?

+   - Seamless model updates. What if we retrain the model on the latest data and need
deploy it quickly, without any interruption to the service?

+   - Serving multiple versions of the model at the same time. What if we want to experiment
with a version of the model that is trained on a different dataset by exposing the
new model to a subset of the users? How do we serve multiple versions of the
model and control proportion of users we see each version?

+   - Model monitoring. How do we track the accuracy of the model as the real estate market
develops? How do we catch and correct problems before they impact our users?

+   - Resiliency and up-time. With this application implemented on a local system, what
happens when the system needs maintenance or has an unplanned outage? How
do we ensure that our users can continue to get access to the application?

We could implement custom code to handle all of these scenarios, but there is a simpler
solution. Public clouds provide complete, end-to-end machine learning and machine
learning operations (MLOps) environments to address all the challenges listed.
The three most-used public clouds in the world are

+   - AWS
- Azure
- Google Cloud

Many organizations will use one or more of these public clouds to put their models
to production.