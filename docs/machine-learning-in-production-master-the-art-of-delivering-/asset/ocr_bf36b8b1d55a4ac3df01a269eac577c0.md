```
| | | | └ test.csv
| | | | └ train.csv
| | | | ├── processing
| | | | │ ├── __init__.py
| | | | │ ├── data_management.py
| | | | │ └ preprocessors.py
| | | | ├── trained_models
| | | | │ ├── __init__.py
| | | | │ └ classification_v1.pkl
| | | | ├── VERSION
| | | | ├── __init__.py
| | | | ├── pipeline.py
| | | | ├── predict.py
| | | | └ train_pipeline.py
| | | └ tests
| | | | ├── pytest.ini
| | | | └ test_predict.py
| | ├── MANIFEST.in
| | ├── README.md
| | ├── requirements.txt
| | ├── setup.py
| | └ tox.ini
|- Dockerfile
|- docker-compose.yml
|- main.py
|- pytest.ini
|- requirements.txt
|- runtime.txt
|- start.sh
|- test.py
└─ tox.ini
```

Let's discuss the code and the concepts from the preceding files. In the `src` directory, files from *Chapter 4: Packaging ML Models* will be used.

# .gitignore

This file contains the names of files and directories that Git should ignore.