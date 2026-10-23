Then when you make a request to the `POST /v1/tokens/authentication` endpoint with a valid email address and password, you should now get a response containing a JWT like this (line breaks added for readability):

```
$ curl -X POST -d '{"email": "faith@example.com", "password": "pa55word"}'
localhost:4000/v1/tokens/authentication
{
    "authentication_token":
"eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJncmVlbmxpZ2h0LmFsFsZXhlZHDcm
RzLm5ldCIsInN1YiI6IjciLCJhdWQiOlsiz3JlZW5saWdodC5hbGV4ZWR3YXJkcy5uZXQiXSwizXh
wIjoxNj
E4OTM4MjY0L jgxOTIwNSwib mJmIjoxNjE4ODUxOD Y0L jgxOTIwNSwiaWF0IjoxNjE4ODUxOD Y0L jg
xOTIwND
    h9.zNK1bJPl5rIr_Yvjy0XuimJwaC3KgPqmW2M1u5RvgeA"
}
```

If you’re curious, you can decode the base64-encoded JWT data. You should see that the content of the claims matches the information that you would expect, similar to this:

```
{"alg":"HS256"}{"iss":"greenlight.alexedwards.net","sub":"7","aud":
["greenlight.alexedwards.net"],
"exp":1618938264.819205,"nbf":1618851864.819205,"iat":1618851864.819204}...
```

Next you’ll need to update the `authenticate()` middleware to accept JWTs in an `Authorization: Bearer <jwt>` header, verify the JWT,