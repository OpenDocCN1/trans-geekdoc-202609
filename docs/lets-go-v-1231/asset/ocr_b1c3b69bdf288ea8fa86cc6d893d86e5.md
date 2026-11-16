```
```go
userPassword: validPassword,
csrToken:     "wrongToken",
wantCode:     http.StatusBadRequest,
},
{
    name:        "Empty name",
    userName:    "",
    userEmail:   validEmail,
    userPassword: validPassword,
    csrToken:    validCSRFToken,
    wantCode:    http.StatusUnprocessableEntity,
    wantFormTag: formTag,
},
{
    name:        "Empty email",
    userName:    validName,
    userEmail:   "",
    userPassword: validPassword,
    csrToken:    validCSRFToken,
    wantCode:    http.StatusUnprocessableEntity,
    wantFormTag: formTag,
},
{
    name:        "Empty password",
    userName:    validName,
    userEmail:   validEmail,
    userPassword: "",
    csrToken:    validCSRFToken,
    wantCode:    http.StatusUnprocessableEntity,
    wantFormTag: formTag,
},
{
    name:        "Invalid email",
    userName:    validName,
    userEmail:   "bob@example.",
    userPassword: validPassword,
    csrToken:    validCSRFToken,
    wantCode:    http.StatusUnprocessableEntity,
    wantFormTag: formTag,
},
{
    name:        "Short password",
    userName:    validName,
    userEmail:   validEmail,
    userPassword: "pa$$",
    csrToken:    validCSRFToken,
    wantCode:    http.StatusUnprocessableEntity,
    wantFormTag: formTag,
},
{
    name:        "Duplicate email",
    userName:    validName,
    userEmail:   "dupe@example.com",
    userPassword: validPassword,
    csrToken:    validCSRFToken,
    wantCode:    http.StatusUnprocessableEntity,
    wantFormTag: formTag,
},
}

for _, tt := range tests {
    t.Run(tt.name, func(t *testing.T) {
        form := url.Values{}
        form.Add("name", tt.userName)
        form.Add("email", tt.userEmail)
        form.Add("password", tt.userPassword)
        form.Add("csrf_token", tt.csrfToken)
```
```