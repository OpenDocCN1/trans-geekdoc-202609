# code/score/score.py

This script will be used for testing the web service. Here, update the saved model path, and then update the input test data that is to be predicted using web service.

The following code update is incorporated into the existing script:

```
1. model_path = Model.get_model_path(model_name="sklearn_classification_model.pkl")
```

Update test data as per the ML model requirement:

```
1. test_row = '{"data":[[1,1,0,1,0,1,2,3849],[1,1,3,0,0,0,1,5540]]}'
```

# aml_config/config.json

Here, you need to update the details from the Azure portal. Other scripts will use the variables declared in this script.

The following code update is incorporated into the existing script:

```
1. {
2.   "subscription_id": "**********",
3.   "resource_group": "mlops",
4.   "workspace_name": "mlops_ws",
5.   "location": "centralus"
6. }
```

# environment_setup/install_requirements.sh

This bash script is responsible for installing Python packages using pip.

The following code update is incorporated into the existing script:

```
1. python --version
2. pip install azure-cli==2.37.0 #==2.0.69
3. pip install --upgrade azureml-sdk[cli]
4. pip install -r requirements.txt
```

# aml_service/00-WorkSpace.py

This file will get the details of the existing workspace; however, if not found, it will create a new one.

# aml_service/10-TrainOnLocal.py

This script triggers the code/training/train.py script to run on the local compute (host agent in case of build pipeline). If you are training on a remote VM, you do not need this script in the build pipeline. All the training scripts generate an output file aml_