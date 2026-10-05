
## 17.2. REDRECTING WITH ALERTS

```go
func getAlert(r *http.Request) *Alert {
  // If its cookie is missing we will assume the alert
  // is invalid and return nil
  lvl, err := r.Cookie("alert_level")
  if err != nil {
    return nil
  }
  msg, err := r.Cookie("alert_message")
  if err != nil {
    return nil
  }
  alert := &Alert{
    Level: lvl.Value,
    Message: msg.Value,
  }
  return alert
}
```

## Redirect function

In order to redirect a user with an alert we need to first persist an alert, then redirect the user. Rather than typing this manually in our controllers we will write a single function to handle the normal both steps for us.

```go
// Redirect accepts all the normal params for an
// http.Redirect performs a redirect, but only after
// persisting the provided alert in a cookie so that it can
// be displayed when the new page is loaded.
func RedirectAlert(w http.ResponseWriter, r *http.Request, urlStr string, code int, alert Alert) {
  persistAlert(w, alert)
  http.Redirect(w, r, urlStr, code)
}
```

Anytime we want to redirect a user with an alert we can call the RedirectAlert function instead of the http.Redirect function.

```go
alert := views.Alert{
  Level: views.AlertLvlSuccess,
  Message: "Welcome to LensLocked!",
}
views.RedirectAlert(w, r, "/galleries", http.StatusFound, alert)
```

## CHAPTER 17. FILLING IN THE GAPS

Note: This last bit of code is an example of how you might redirect a user with an alert after they sign up for a new account.

## Rendering persisted alerts

Without informing our views of persisted alerts they wouldn't serve any purpose. We need to update the Render method of the View type to inform it of the alerts and have it check for any persisted alerts. It will also be responsible for clearing any alerts after rendering so a user doesn’t see the same alert several times in a row.

```bash
$ atom views/view.go
```

Find the Render method and update it with the following code.

```go
func (v *View) Render(w http.ResponseWriter, r *http.Request, data interface{}) {
	w.Header().Set("Content-Type", "text/html")
	var vd
	switch d := data.(type) {
	// ... this is unchanged
	// Lookup the alert and assign it if one is persisted
	if alert := getAlert(r); alert != nil {
		vd.Alert = alert
		clearAlert(w)
	}
	vd.User = context.User(r.Context())
	// ... everything below this point is unchanged
}
```

Note: All we are adding here is the "if alert := getAlert(r)..." block which is 4 lines long. Everything else in the Render method remains unchanged.

We now have all the tools necessary to redirect users with an alert message.

## 17.3. EMAILING USERS

### Source code

The links below have the completed source code and a diff of all the code changed in this section.
Completed - book.usegolang.com/17.2
Changes - book.usegolang.com/17.2-diff

## 17.3 Emailing users

Emailing users is a tricky feature to write about because everyone does it differently. Some companies write their own tools to manage sending emails to customers, while others use a variety of services like Mailgun and Sendgrid.
I personally tend to use Mailgun, which is free for your first 10k emails (as of this writing) while also being simple to use. As a result, that is what we will be using in this section of the course.

> **Box 17.1. Why don't we use the net/smtp package?**

It is inevitable that some readers will be upset by my decisions to use a third party service in this book rather than covering the net/smtp package in the standard library.
I am opting to use a third party service because the purpose of this course is to teach you how to build a real web application, and real web applications that I have involved with almost all use a third party service for email delivery. Not only is it easier to avoid your emails being flagged as spam this way, but their APIs make it easier to deliver email without having to learn about the specifics of SMTP, which is not the purpose of this course.

The first thing you will need to do is head over to their website, create an account, and setup a domain to send email from.

https://www.mailgun.com/

After your account is setup, we need to install the Go client provided by the Mailgun team.

```bash
$ go get gopkg.in/mailgun/mailgun-go.v1
```

Next you will need to update your config source code to add a section for Mailgun.

```bash
$ atom config.go
```

```go
type Config struct {
	Port int `json:"port"`
	Env string `json:"env"`
	Pepper string `json:"pepper"`
	HMACKey string `json:"hmac_key"`
	Database PostConfig `json:"Database"`
	Mailgun MailgunConfig `json:"mailgun"`
}

type MailgunConfig struct {
	APIKey string `json:"api_key"`
	PublicAPIKey string `json:"public_api_key"`
	Domain string `json:"domain"`
}
```

Anytime we want to redirect a user with an alert we can call the RedirectAlert function instead of the http.Redirect function.

```go
alert := views.Alert{
  Level: views.AlertLvlSuccess,
  Message: "Welcome to LensLocked!",
}
views.RedirectAlert(w, r, "/galleries", http.StatusFound, alert)
```

## 17.3 Emailing users

Emailing users is a tricky feature to write about because everyone does it differently. Some companies write their own tools to manage sending emails to customers, while others use a variety of services like Mailgun and Sendgrid.
I personally tend to use Mailgun, which is free for your first 10k emails (as of this writing) while also being simple to use. As a result, that is what we will be using in this section of the course.

> **Box 17.1. Why don't we use the net/smtp package?**

It is inevitable that some readers will be upset by my decisions to use a third party service in this book rather than covering the net/smtp package in the standard library.
I am opting to use a third party service because the purpose of this course is to teach you how to build a real web application, and real web applications that I have involved with almost all use a third party service for email delivery. Not only is it easier to avoid your emails being flagged as spam this way, but their APIs make it easier to deliver email without having to learn about the specifics of SMTP, which is not the purpose of this course.

The first thing you will need to do is head over to their website, create an account, and setup a domain to send email from.

https://www.mailgun.com/

After your account is setup, we need to install the Go client provided by the Mailgun team.

```bash
$ go get gopkg.in/mailgun/mailgun-go.v1
```

Next you will need to update your config source code to add a section for Mailgun.

```bash
$ atom config.go
```

```go
type Config struct {
	Port int `json:"port"`
	Env string `json:"env"`
	Pepper string `json:"pepper"`
	HMACKey string `json:"hmac_key"`
	Database PostConfig `json:"Database"`
	Mailgun MailgunConfig `json:"mailgun"`
}

type MailgunConfig struct {
	APIKey string `json:"api_key"`
	PublicAPIKey string `json:"public_api_key"`
	Domain string `json:"domain"`
}
```

## 17.3 EMAILING USERS

### Source code

The links below have the completed source code and a diff of all the code changed in this section.
Completed - book.usegolang.com/17.2
Changes - book.usegolang.com/17.2-diff

## 17.4. PERSISTING AND PREFILLING FORM DATA

### Source code

The links below have the completed source code and a diff of all the code changed in this section.
Completed - book.usegolang.com/17.3
Changes - book.usegolang.com/17.3-diff
