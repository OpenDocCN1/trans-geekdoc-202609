```
{
  "user": {
    "id": 4,
    "created_at": "2021-04-11T21:21:12+02:00",
    "name": "Carol Smith",
    "email": "carol@example.com",
    "activated": false
  }
}

Time: 0.268639
```

This time, you should see that the time taken to return the response is much faster — in my case 0.27 seconds compared to the previous 2.33 seconds.

And if you take a look at your Mailtrap inbox, you should see that the email for `carol@example.com` has been delivered correctly. Like so: