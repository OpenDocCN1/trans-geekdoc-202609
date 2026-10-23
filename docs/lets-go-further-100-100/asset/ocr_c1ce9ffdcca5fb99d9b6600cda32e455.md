```
"error": "invalid authentication credentials"
}
```

Before we continue, let’s quickly have a look at the `tokens` table in our PostgreSQL database to check that the authentication token has been created.

```
$ psql $GREENLIGHT_DB_DSN
Password for user greenlight:
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256,
compression: off)
Type "help" for help.

greenlight=> SELECT * FROM tokens WHERE scope = 'authentication';
\x4390d2ff4af7346dd4238ffccb8a5b18e8c3af9aa8cf57852895ad0f8ee2c50d |     1 | 2021-04-
17 11:03:37+02 | authentication
```

That’s looking good. We can see that the token is associated with the user with ID 1 (which if you’ve been following along will be the user `alice@example.com`) and has the correct scope and expiry time.

# Additional Information

# The Authorization header

Occasionally you might come across other APIs or tutorials where authentication tokens are sent back to the client in an `Authorization` header, rather than in the response body like we are in this chapter.