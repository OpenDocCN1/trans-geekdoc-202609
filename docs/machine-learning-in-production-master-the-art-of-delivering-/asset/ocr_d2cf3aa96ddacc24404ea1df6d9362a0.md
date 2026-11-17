```
13. setuptools==40.6.3
14. wheel==0.32.3
```

# classification_v1.pkl

This is a pickled file from the trained model.

# train_pipeline.py

This module loads the training data and passes it to the pipeline, then saves the pickle file of the model to the local directory.

```
1. #Import Libraries
2. import pandas as pd
3. import numpy as np
4.
5. #Import other files/modules
6. from prediction_model.config import config
7. from prediction_model.processing.data_management import load_dataset, save_pipeline
8. import prediction_model.processing.preprocessors as pp
9. import prediction_model.pipeline as pl
10. from prediction_model.predict import make_prediction
11.
12. def run_training():
13. """Train the model"""
14. #Read Data
15. train = load_dataset(config.TRAIN_FILE)
16.
17. #separating Loan_status in y
18. y = train[config.TARGET].map({'N':0 , 'Y':1})
19. pl.loan_pipe.fit(train[config.FEATURES],y)
20. save_pipeline(pipeline_to_save=pl.loan_pipe)
```