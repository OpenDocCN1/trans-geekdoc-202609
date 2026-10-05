# 9. Testing REST Controllers

You can also test your REST controllers easily. The examples in this chapter will use CodeIgniter Rest Server.

# 9.1 Installing CodeIgniter Rest Server

**CodeIgniter Rest Server** is a fully RESTful server implementation for CodeIgniter.
Download the latest version (in this book we use v2.7,2) by https://github.com/chriskacerguis/codeigniter-restserver/releases and unzip it. Copy the following files into your CodeIgniter/application directory from the corresponding directory in the Zip package.

```
CodeIgniter/
└── application/
    ├── config/
    │   └── rest.php
    ├── controller/
    │   └── api/
    │       └── Example.php
    └── libraries/
        └── Format.php
    └── REST_Controller.php
```

CodeIgniter Rest Server is licensed under the MIT License. See the [License Agreement for CodeIgniter Rest Server](https://github.com/chriskacerguis/codeigniter-restserver/blob/master/LICENSE).

# Fixing the CodeIgniter Rest Server Code

Up to the present we have never modified code to write tests, because we don't normally have to do so. However, we have to modify CodeIgniter Rest Server in order to be able to write tests.

> **Testing Tip: Untestable Code**
If you can't write tests or it is hard to write tests, it is a sign that your application code design should be improved.

First, replace require with `require_once` in the Example controller. If there is more than one REST controller, we load them at the same time during execution, which will result in *Fatal error: Cannot redeclare class REST_Controller* if require is used.