However, the API key does not yet have anything directly to do with authentication. To do this, you create so-called OAuth client IDs. Google expects such a client ID for every application or mobile app with which you want to access the API. For our example, we select web application for the application type, as we want to access the application via the web using PHP.

An OAuth client ID consists of several components: first, the client ID itself, and second, a client key or client secret. We need these two pieces of data in our PHP application in order to later access the API in our project, the one for Google Drive, via OAuth. To use them, Google offers a convenient function: As soon as you have created the client ID, a Download icon appears in the Credentials view. The download provides a finished JSON file with the data relevant to the project and application:

```
{
 "web":
 {
 "client_id": "xyz.apps.googleusercontent.com",
 "project_id": "rheinwerk-php",
 "auth_uri": "https://accounts.google.com/o/oauth2/auth",
 "token_uri": "https://oauth2.googleapis.com/token",
 "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
 "client_secret": "xyz"
 }
}
```

By default, the JSON file uses the client ID as its name. For the sake of simplicity, we rename it to client_secrets.json.

> Note
> 
> Another security function is hidden behind the Authorized Redirect URIs setting in the OAuth client ID. Here you should enter all addresses to which Google should redirect after authorization by the user. In our case, for example, this would be the local address: http://localhost/php/oauth2callback.php. If you overlook this, you will receive a corresponding error message when testing with a user during redirection.

# Configure Consent Screen

As your application will later ask the user for their consent to access their data via the API, you still need to take care of the so-called consent screen (also known as the user consent screen) in the Google project. In fact, Google even forces you to do this before you can create the first OAuth client ID.

Many important settings for the project are hidden behind the approval screen: First, you define which users can access the project. Internal users are only possible if you use