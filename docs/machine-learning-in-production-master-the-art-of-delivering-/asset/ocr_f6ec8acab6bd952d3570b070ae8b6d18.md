```
requirements.txt
setup.py
tox.ini
+--prediction_model
|   |   pipeline.py
|   |   predict.py
|   |   train_pipeline.py
|   |   VERSION
|   |   __init__.py
|   +---config
|   |   |   config.py
|   |   __init__.py
|   +---datasets
|   |   |   test.csv
|   |   |   train.csv
|   |   __init__.py
|   +---processing
|   |   |   data_management.py
|   |   |   preprocessors.py
|   |   __init__.py
|   \---trained_models
|       classification_v1.pkl
|       __init__.py
\---tests
    pytest.ini
    test_predict.py
```

# main.py

FastAPI is a web framework for developing RESTful APIs in Python. Create a main.py file to run the FastAPI app.

> Note: FastAPI requires Python 3.6+.