```
greenlight=> SELECT * FROM tokens;
               hash               | user_id
|       expiry       |  scope
---------------------------------+---------
-+---------------+----------------
\x09bcb40206b25fe511bfe f4d56cbe8c4a141869fc29612fa984b371ef086f5f5 | 7
| 2021-04-18 20:25:41+02 | activation
```

We can see here that the activation token hash is displayed as the value:

```
09bcb40206b25fe511bfe f4d56cbe8c4a141869fc29612fa984b371ef086f5f5
```

As we mentioned earlier, `psql` always displays values in `bytea` columns as a hex-encoded string. So what we’re seeing here is a *hexadecimal encoding of the SHA-256 hash of the plaintext token* `P4B3URJZJ2NW5UPZC2OHN4H2NM` that we sent in the welcome email.

> **Note:** If you want, you can verify that this is correct by entering a plaintext activation token from the welcome email into this online SHA-256 hash generator. You should see that the result matches the hex-encoded value inside your PostgreSQL database.

Notice too that the `user_id` value of 7 is correct for our `faith@example.com` user, the expiry time has been correctly set to