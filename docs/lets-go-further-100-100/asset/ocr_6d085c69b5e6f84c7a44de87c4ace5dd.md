+   - . or _. If you want to include these files you should use the * wildcard character in the path, like `//go:embed "templates/*"`
+   - You can specify multiple directories and files in one directive. For example: `//go:embed "images" "styles/css" "favicon.ico"`.
+   - The path separator should always be a forward slash, even on Windows machines.

# Using our mail helper

Now that our email helper package is in place, we need to hook it up to the rest of our code in the `cmd/api/main.go` file. Specifically, we need to do two things:

+   - Adapt our code to accept the configuration settings for the SMTP server as command-line flags.
+   - Initialize a new `Mailer` instance and make it available to our handlers via the `application` struct.

If you’re following along, please make sure to use your own Mailtrap SMTP server settings from the previous chapter as the default values for the command line flags here — not the exact values I’m using in the code below.

```
File: cmd/api/main.go

```go
package main
```
```