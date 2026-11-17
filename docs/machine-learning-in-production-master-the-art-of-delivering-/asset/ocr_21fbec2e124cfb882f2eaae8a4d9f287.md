To run the **pytest**, simply switch to the package directory and run the following command:

```
pytest
```

It searches for _test\*.py or *_test.py files.

The **pytest** output can be any of the following:

+   - A dot (.) means that the test has passed.
+   - An F means that the test has failed.
+   - An E means that the test raised an unexpected exception.

```
pytest -v
```

\-v or --verbose flag allows you to see whether individual tests are passing or failing.

# # pytest fixtures

pytest fixtures are basic functions, and they run before the test functions are executed. pytest fixtures are useful when you are running multiple test cases with the same function return value.

It can be declared by the @pytest.fixture marker. The following is an example:

```
1. @pytest.fixture
2. def xyz_func():
3.    return "ABC"
```

When pytest runs a test case, it looks at the parameters in that test function’s signature and then searches for fixtures that have the same names as those parameters. Once pytest finds them, it runs those fixtures, captures what they returned (if any), and passes those objects into the test functions as arguments.

You can configure **pytest** using the _pytest.ini file.

# # Python packaging and dependency management

Suppose you have created the final ML model in a Python notebook. This Python notebook holds all the steps right from loading the data to predicting the test data.

However, this notebook should not be used in the production environment for the following reasons: