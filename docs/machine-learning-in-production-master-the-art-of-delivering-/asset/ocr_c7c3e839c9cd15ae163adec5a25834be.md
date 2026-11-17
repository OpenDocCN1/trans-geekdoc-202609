```
15.
16. response = client.post("/predict_status", json=data)
17. assert response.json()["status"] != ''
18. assert response.json() == {"status": "Approved"}
```

# tox.ini

This is the tox configuration file. The tox automates and standardizes the testing in Python. It is a virtualenv management and test command-line tool to check whether your package is compatible with different Python versions. The tox will first create a virtual environment based on the configuration provided and then install dependencies. Finally, it will execute the commands provided in the configuration.

**tox-gh-actions** is a plugin that enables tox to run on GitHub Actions. Hence, you need to install **tox-gh-actions** in the GitHub Actions workflow before running the tox command.

This file will check the package compatibility with Python-3.7. First, it will install the required dependencies and then run the pytest commands.

```
1. [tox]
2. envlist = py37
3. skipsdist=True
4.
5. [gh-actions]
6. python =
7. 3.7: py37
8.
9. [testenv]
10. install_command = pip install {opts} {packages}
11. deps =
```