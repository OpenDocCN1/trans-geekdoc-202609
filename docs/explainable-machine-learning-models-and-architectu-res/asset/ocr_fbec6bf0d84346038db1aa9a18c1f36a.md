![](bbox=[0.222, 0.102, 0.777, 0.591])

Figure 9.1 Django's MVT.

```
path("register/success/", views.regsuccess, name="regsuccess")
```

Figure 9.2 Website architecture.

```
def regsuccess(request):
    num_visits = request.session.get('num_visits', 1)
    request.session['num_visits'] = num_visits + 1
    print(num_visits)
    return render(request, "regsuccess.html")
```

Figure 9.3 View function defined in views.py for URL (register/success/) of urls.py in the project.