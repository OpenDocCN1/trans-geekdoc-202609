Add error handling functionality, as follows:

```
1. @app.errorhandler(500)
2. def internal_error(error):
3.     return "500: Something went wrong"
4.
5. @app.errorhandler(404)
6. def not_found(error):
7.     return "404: Page not found",404
```

Finally, you will define the main function as shown below:

```
1. if __name__ == '__main__':
2.     app.run(host='0.0.0.0', port=port)
```

# # Gunicorn

The Gunicorn is an application server for running a Python app. Gunicorn is WSGI compatible, so it can communicate with multiple WSGI applications. In the current case, Gunicorn translates the request received from Nginx for the Flask app and vice versa.

To install Gunicorn, execute the following command:

```
sudo apt-get install gunicorn3
```

Go to the directory where the app.py file is located and run:

```
gunicorn3 app:app
```

This command helps to know which IP and port are being used by Gunicorn. In this case, it is 8000 and IP can be 0.0.0.0 or 127.0.0.1.

# # NGINX

NGINX is a high-performance, highly scalable open-source, and reverse proxy web server. It can perform load balancing and caching application instances. It accepts incoming connections and decides where they should go next. In the current case, it sits on top of a Gunicorn.

To install NGINX, execute the following command:

```
sudo apt-get install nginx
```