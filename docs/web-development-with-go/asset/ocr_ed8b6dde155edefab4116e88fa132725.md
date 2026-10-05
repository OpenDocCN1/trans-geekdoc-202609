# 6.3. CREATING A REUSABLE BOSTRAP LAYOUT

Update both the home and contact templates using the code in Listing 6.9 and Listing 6.10.

| Listing 6.9: Home template with a footer. |
| <h1>Welcome to my awesome site!</h1> |
| {{template "footer"}} | |

| Listing 6.10: Contact template with a footer. |
| To get in touch, please send an email to <a href="mailto:support@lenslocked.com">support@lenslocked.com</a>. |
| {{template "footer"}} | |

Stop (ctrl + c) and restart your server, then navigate to the home and contact pages to see if the footer is being rendered.

```
$ go run main.go
```

If everything is working, you should see a footer on both pages similar to the one in Figure 6.1.