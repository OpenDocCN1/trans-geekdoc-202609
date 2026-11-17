+   1. venv/
+   2. __pycache__/
+   3. .pytest_cache
+   4. .tox

# main.py

This file will load the pickle object of the model and run a FastAPI app. First, load the dependencies and modules from **prediction_model**:

```
1. # Importing Dependencies
2. from fastapi import FastAPI
3. from pydantic import BaseModel
4. import uvicorn
5. import pickle
6. import os
7. import numpy as np
8. import pandas as pd
9. from fastapi.middleware.cors import CORSMiddleware
10. from prediction_model.predict import make_prediction
11. import pandas as pd
```

Create a FastAPI instance and assign it to the **app** so that the **app** becomes a point of interaction while creating the API.

```
1. app = FastAPI(
2.     title="Loan Prediction Model API",
3.     description="A simple API that uses ML model to predict the Loan application status",
4.     version="0.1",
5. )
```

**CORS (Cross-Origin Resource Sharing)** refers to the situations when a front end running in a browser has JavaScript code that communicates with a back end, and the back end is of a different origin than the front end. However, it depends on your application and requirement whether to use it.

```
1. origins = [
```