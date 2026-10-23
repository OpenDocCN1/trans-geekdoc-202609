future, we can simply make an additional file in our `internal/mailer/templates` folder with the email content, and then send it from our handlers in the same way that we have done here.

# Additional Information

# Retrying email send attempts

If you want, you can make the email sending process a bit more robust by adding some basic ‘retry’ functionality to the `Mailer.Send()` method. For example:

```
```go
func (m Mailer) Send(recipient, templateFile string, data interface{}) error
{
    ...

    // Try sending the email up to three times before aborting and returning
    the final
    // error. We sleep for 500 milliseconds between each attempt.
    for i := 1; i <= 3; i++ {
        err = m.dialer.DialAndSend(msg)
        // If everything worked, return nil.
        if nil == err {
            return nil
        }

        // If it didn't work, sleep for a short time and retry.
        time.Sleep(500 * time.Millisecond)
    }
}
```
```