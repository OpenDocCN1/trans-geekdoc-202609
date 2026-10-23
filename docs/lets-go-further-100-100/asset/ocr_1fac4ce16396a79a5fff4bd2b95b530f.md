You’ll also need to create an `internal/mailer/templates/token_activation.tmpl` file containing the necessary email templates, similar to this:

```
File: internal/mailer/templates/token_activation.tmpl

{{define "subject"}}Activate your Greenlight account{{end}}

{{define "plainBody"}}
Hi,

Please send a `PUT /v1/users/activated` request with the following JSON body to activate your account:

{"token": "{{.activationToken}}"}

Please note that this is a one-time use token and it will expire in 3 days.

Thanks,

The Greenlight Team
{{end}}

{{define "htmlBody"}}
<!doctype html>
<html>
    <head>
        <meta name="viewport" content="width=device-width" />
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    </head>
    <body>
        <p>Hi,</p>
        <p>Please send a <code>PUT /v1/users/activated</code> request with the following JSON body to activate your account:</p>
        <pre><code>
        {"token": "{{.activationToken}}"}

```