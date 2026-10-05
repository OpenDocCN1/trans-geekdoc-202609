
# Integration with Social Media Logins

Users' existing Facebook and Google accounts can also be utilized to streamline the authentication and registration process when social media logins are integrated into a web application. In particular, for our `gitforgits.com`, letting users log in through these services can improve the user experience by giving them a safer and faster alternative rather than creating and remembering a new set of credentials.

## Integration with Google Login

We already set up the basic OAuth2 configuration for Google in our previous example. After the user is authenticated and you receive the OAuth token, you typically want to fetch user data from Google to create a user session. Given below is how to modify the `handleGoogleCallback` function to fetch user details:

```go
import (
    "encoding/json"
    "golang.org/x/oauth2"
    "io/ioutil"
    "net/http"
)
```

This would be part of the `googleOauthConfig` setup

```go
var googleOauthConfig = &oauth2.Config{
    // previous configuration...
}
```

```go
func handleGoogleCallback(w http.ResponseWriter, r *http.Request) {
    content, err := getUserDataFromGoogle(r.FormValue("code"))
    if err != nil {
        http.Error(w, err.Error(), http.StatusInternalServerError)
        return
    }
    fmt.Fprintf(w, "User Info: %s", content)
}
```

```go
func getUserDataFromGoogle(code string) (string, error) {
    // Exchange the code for a token
    token, err := googleOauthConfig.Exchange(oauth2.NoContext, code)
    if err != nil {
        return "", err
    }
    // Create a client to use the token
    client := googleOauthConfig.Client(oauth2.NoContext, token)
    response, err := client.Get("https://www.googleapis.com/oauth2/v2/userinfo")
    if err != nil {
        return "", err
    }
    defer response.Body.Close()
    data, err := ioutil.ReadAll(response.Body)
    if err != nil {
        return "", err
    }
    return string(data), nil
}
```

In this code snippet, after exchanging the code for a token, we use the token to create an authenticated client. This client is then used to make a request to Google's user info endpoint, which returns details like the user's email, name, and profile picture.

## Integration with Facebook Login

Integrating Facebook login involves steps similar to those for Google. First, you need to set up an application in the Facebook developer console, get your app credentials, and configure the OAuth2 setup in your Go application.

### Setting up Facebook OAuth Configuration

```go
var facebookOauthConfig = &oauth2.Config{
    RedirectURL: "http://localhost:8080/oauth2/facebook/callback",
    ClientID: "YOUR_FACEBOOK_CLIENT_ID",
    ClientSecret: "YOUR_FACEBOOK_CLIENT_SECRET",
    Scopes: []string{"email"},
    Endpoint: oauth2.Endpoint{
        AuthURL: "https://www.facebook.com/v2.8/dialog/oauth",
        TokenURL: "https://graph.facebook.com/v2.8/oauth/access_token",
    },
}
```

### Handling Facebook Callback

The callback handler for Facebook would look quite similar to the Google one, but you would fetch user data from Facebook's graph API:

```go
func handleFacebookCallback(w http.ResponseWriter, r *http.Request) {
    content, err := getUserDataFromFacebook(r.FormValue("code"))
    if err != nil {
        http.Error(w, err.Error(), http.StatusInternalServerError)
        return
    }
    fmt.Fprintf(w, "User Info: %s", content)
}
```

```go
func getUserDataFromFacebook(code string) (string, error) {
    token, err := facebookOauthConfig.Exchange(oauth2.NoContext, code)
    if err != nil {
        return "", err
    }
    // Fetch user data from Facebook's graph API
    client := facebookOauthConfig.Client(oauth2.NoContext, token)
    response, err := client.Get("https://graph.facebook.com/me?fields=id,name,email")
    if err != nil {
        return "", err
    }
    defer response.Body.Close()
    data, err := ioutil.ReadAll(response.Body)
    if err != nil {
        return "", err
    }
    return string(data), nil
}
```

## Integration with Email Login

While social logins are convenient, providing an option for users to register and log in using their email address is also essential. This involves setting up a traditional registration and login form where users can enter their email and password. You would typically have an HTML form for registration and login that posts to your Go server. On the server side, you handle these posts, create new user records for registrations, and validate credentials for logins.

```go
func handleRegistration(w http.ResponseWriter, r *http.Request) {
    // Extract user details from r.FormValue("email"), r.FormValue("password")
    // Create user logic here
    fmt.Fprintln(w, "Registration successful")
}
```

```go
func handleLogin(w http.ResponseWriter, r *http.Request) {
    // Validate login credentials
    // Authenticate session
    fmt.Fprintln(w, "Login successful")
}
```

Apps can provide users with more login options by combining OAuth2 with social media and supporting traditional email login methods. This gives users more control over their experience on the site and makes logging in easier, both of which improve the user experience.
