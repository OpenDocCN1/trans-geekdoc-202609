# 2.2. DEMSTIFYING OUR APP

First, we declare the function main(). This is the function that will be run to start up your application, it needs to call any other code that you want to run.

Inside the main function we do two things. First we set our handlerFunc as the function we want to use to handle web requests to our server with the path /. This covers all paths that the user might try to visit on our website, so you could also visit http://localhost:3000/some-other-path and it would also be processed by handlerFunc.

Lastly, we call http.ListenAndServe(":3000", nil), which starts up a web server listening on port 3000 using the default http handlers.

Box 2.7. Port 3000 and localhost.

If this is your first time seeing things like localhost : 3000 they might seem confusing at first, but don’t worry! They are actually pretty simple to understand.

In computer networking, the term localhost was created to mean “computer”. When we talk about visiting http://localhost:3000/ in your browser, what we are really telling the browser “try to load a web page from this computer at port 3000”.

The port comes from the last part of the URL; The : 3000 portion. When you type www.google.com into your browser you don’t have to include a port because the browser will use a default port automatically, but you could type it explicitly if you wanted. Try going to http://www.google.com:80.

We don’t have to use port 3000 locally. In fact, many developers use port 8080 for local development. I simply opted to use port 3000 because it is what I am used to.