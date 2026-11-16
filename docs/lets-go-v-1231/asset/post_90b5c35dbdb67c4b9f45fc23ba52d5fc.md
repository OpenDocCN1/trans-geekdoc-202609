
sql: Scan error on column index 3, name "created": unsupported Scan, storing driver.Value type []uint8 into type *time.Time

goroutine 51 [running]:
runtime/debug.Stack()
	/usr/local/go/src/runtime/debug/stack.go:24 +0x65
main.(*application).serverError(/src/web/cmd/web/server.go:60 +0x68
main.(*application).snippetbox(/cmd/web/cmd/web/helpers.go:16 +0x66
main.(*application).home(/cmd/web/cmd/web.go:50 +0x84
net/http.HandlerFunc.ServeHTTP(/x/b64e8...

Running the application again without the -debug flag should result in a generic "Internal Server Error" message.

## Suggested code

### Suggested code for step 1

File: cmd/web/main.go

```
package main

type application struct {
	debug       bool // Add a new debug field.
	logger      *slog.Logger
	snippets    models.SnippetModelInterface
	users       models.UserModelInterface
	templateCache map[string]*template.Template
	formDecoder  *form.Decoder
	sessionManager *scs.SessionManager
}

func main() {
	addr := flag.String("addr", ":4000", "HTTP network address")
	dsn := flag.String("dsn", "web:pass@/snippetbox?parseTime=true", "MySQL data source name")
	// Create a new debug flag with the default value of false.
	debug := flag.Bool("debug", false, "Enable debug mode")

	flag.Parse()

	logger := slog.New(slog.NewTextHandler(os.Stdout, nil))

	db, err := openDB(*dsn)
	if err != nil {
		logger.Error(err.Error())
		os.Exit(1)
	}

	defer db.Close()

	templateCache, err := newTemplateCache()
	if err != nil {
		logger.Error(err.Error())
		os.Exit(1)
	}

	formDecoder := form.NewDecoder()

	sessionManager := scs.New()
	sessionManager.Store = mysqlstore.New(db)
	sessionManager.Lifetime = 12 * time.Hour
	sessionManager.Cookie.Secure = true

	app := &application{
		debug:      *debug, // Add the debug flag value to the application struct.
		logger:     logger,
		snippets:   &models.SnippetModel{DB: db},
		users:      &models.UserModel{DB: db},
		templateCache: templateCache,
		formDecoder:   formDecoder,
		sessionManager: sessionManager,
	}

	tlsConfig := &tls.Config{
		CurvePreferences: []tls.CurveID{tls.X25519, tls.CurveP256},
	}

	srv := &http.Server{
		Addr:         *addr,
		Handler:      app.routes(),
		ErrorLog:     slog.NewLogLogger(logger.Handler(), slog.LevelError),
		TLSConfig:    tlsConfig,
		IdleTimeout:  time.Minute,
		ReadTimeout:  5 * time.Second,
		WriteTimeout: 10 * time.Second,
	}

	logger.Info("starting server", "addr", srv.Addr)

	err = srv.ListenAndServeTLS("./tls/cert.pem", "./tls/key.pem")
	logger.Error(err.Error())
	os.Exit(1)
}
...
```

## Suggested code for step 2

File: cmd/web/helpers.go

...

```
func (app *application) serverError(w http.ResponseWriter, r *http.Request, err error) {
	var (
		method = r.Method
		uri    = r.URL.RequestURI()
		trace  = string(debug.Stack())
	)

	app.logger.Error(err.Error(), "method", method, "uri", uri)

	if app.debug {
		body := fmt.Sprintf("%s\n%s", err, trace)
		http.Error(w, body, http.StatusInternalServerError)
		return
	}

	http.Error(w, http.StatusText(http.StatusInternalServerError), http.StatusInternalServerError)
}

...
```

## Test the snippetCreate handler

Your goal in this exercise is to create an end-to-end test for the `GET /snippet/create` route. Specifically, you want to test that:

- Unauthenticated users are redirected to the login form.
- Authenticated users are shown the form to create a new snippet.

### Step 1

Create a new `TestSnippetCreate` test in your `cmd/web/handlers_test.go` file. In this test, use the pattern and helpers from the end-to-end testing chapter to initialize a new test server using the application routes and mocked dependencies.

Show suggested code

### Step 2

Create a sub-test with the name "Unauthenticated". In this sub-test, make a `GET /snippet/create` request against the test server as an unauthenticated user. Verify that the response has the status code 303 and a `Location: /user/login` header. Again, reuse the helpers that we made in the end-to-end testing chapter.

Show suggested code

### Step 3

Create another sub-test with the name "Authenticated". In this sub-test, mimic the workflow of logging in as a user to authenticate. Specifically, you'll need to make a `GET /user/login` request, extract the CSRF token from the response body, then make a `POST /user/login` request using the credentials in the mock user model (email of "alice@example.com", password of "pa$$word").

Then once you've authenticated, make a `GET /snippet/create` request and verify that you receive the status code 200 and an HTML body including the text `<form action='/snippet/create' method='POST'>`.

Show suggested code

## Suggested code

### Suggested code for step 1

File: cmd/web/handlers_test.go

...

```
func TestSnippetCreate(t *testing.T) {
	app := newTestApplication(t)
	ts := newTestServer(t, app.routes())
	defer ts.Close()
}
```

### Suggested code for step 2

File: cmd/web/handlers_test.go

...

```
func TestSnippetCreate(t *testing.T) {
	app := newTestApplication(t)
	ts := newTestServer(t, app.routes())
	defer ts.Close()

	t.Run("Unauthenticated", func(t *testing.T) {
		code, headers, _ := ts.get(t, "/snippet/create")

		assert.Equal(t, code, http.StatusSeeOther)
		assert.Equal(t, headers.Get("Location"), "/user/login")
	})
}
```

```shell
$ go test -v -run=TestSnippetCreate ./cmd/web/
=== RUN   TestSnippetCreate
=== RUN   TestSnippetCreate/Unauthenticated
--- PASS: TestSnippetCreate (0.01s)
    --- PASS: TestSnippetCreate/Unauthenticated (0.00s)
PASS
ok      snippetbox.alexedwards.net/cmd/web        0.010s
```

### Suggested code for step 3

```go
File: cmd/web/handlers_test.go

...

func TestSnippetCreate(t *testing.T) {
	app := newTestApplication(t)

	ts := newTestServer(t, app.routes())
	defer ts.Close()

	t.Run("Unauthenticated", func(t *testing.T) {
		code, headers, _ := ts.get(t, "/snippet/create")

		assert.Equal(t, code, http.StatusSeeOther)
		assert.Equal(t, headers.Get("Location"), "/user/login")
	})

	t.Run("Authenticated", func(t *testing.T) {
		// Make a GET /user/login request and extract the CSRF token from the
		// response.
		_, _, body := ts.get(t, "/user/login")
		csrfToken := extractCSRFToken(t, body)

		// Make a POST /user/login request using the extracted CSRF token and
		// credentials from our mock user model.
		form := url.Values{}
		form.Add("email", "alice@example.com")
		form.Add("password", "pa$$word")
		form.Add("csrf_token", csrfToken)
		ts.postForm(t, "/user/login", form)

		// Then check that the authenticated user is shown the create snippet
		// form.
		code, _, body := ts.get(t, "/snippet/create")

		assert.Equal(t, code, http.StatusOK)
		assert.StringContains(t, body, "<form action='/snippet/create' method='POST'>")
	})
}
```

```shell
$ go test -v -run=TestSnippetCreate ./cmd/web/
=== RUN   TestSnippetCreate
=== RUN   TestSnippetCreate/Unauthenticated
=== RUN   TestSnippetCreate/Authenticated
--- PASS: TestSnippetCreate (0.01s)
    --- PASS: TestSnippetCreate/Unauthenticated (0.00s)
    --- PASS: TestSnippetCreate/Authenticated (0.00s)
PASS
ok      snippetbox.alexedwards.net/cmd/web  0.012s
```

## Add an ‘Account’ page to the application

Your goal for this exercise is to add a new ‘Your Account’ page to the application. It should be mapped to a new GET /account/view route and display the name, email address, and signup date for the currently authenticated user, similar to this:

![](img/c3e650db0d8dfdecc0f8e34a67719f65_417_0.png)

### Step 1

In the internal/models/users.go file create a new UserModel.Get() method. This should accept the ID of a user as a parameter, and return a User struct containing all the information for this user (except for their hashed password, which we don’t need). If no user is found with the ID, it should return an ErrNoRecord error.

Also, update the UserModelInterface type to include this new Get() method, and add a corresponding method to our mock mocks.UserModel so that it continues to satisfy the interface.
