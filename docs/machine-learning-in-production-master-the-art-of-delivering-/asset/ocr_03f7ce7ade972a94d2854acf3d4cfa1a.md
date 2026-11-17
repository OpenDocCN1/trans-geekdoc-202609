register as production model perform better written inside the **except** block and exit from the code.

If the run id is found in `aml_config/run_id.json`, it will register the model. Finally, it will write the registered model details to `/aml_config/model.json`.

The following code update is incorporated into the existing script:

```
1. # Download Model to Project root directory

2. model_name = "sklearn_classification_model.pkl"

3. run.download_file(

4.     name="./outputs/" + model_name, output_file_path="./model/" + model_name

    model_name

5. )

6. print("Downloaded model {} to Project root directory".format(model_name))

7. os.chdir("./model")

8. model = Model.register(

9.     model_path=model_name, # This points to a local file

10.    model_name=model_name, # This is the name the model is registered as

11.    tags={"area": "loan", "type": "classification", "run_id": run_id},

12.    description="Classification model for loan dataset",

13.    workspace=ws,

14. )
```

# aml_service/30-CreateScoringImage.py

In the beginning, it will look for the `aml_config/model.json` file generated from the previous step. If it is not found, the script will be terminated with the message **No new model to register thus no need to create new scoring image**.

The following code update is incorporated into the existing script:

```
1. image_name = "loan-model-score"

2.

3. image_config = ContainerImage.image_configuration(

4.     execution_script="score.py",

5.     runtime="python-slim",
```