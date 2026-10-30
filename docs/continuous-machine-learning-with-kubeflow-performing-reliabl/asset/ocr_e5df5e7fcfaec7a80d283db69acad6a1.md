```
print(new_model.summary())
predictions = new_model.predict(validation)
predictions = [1 if x>0.5 else o for x in predictions]
```

```
accuracy = accuracy_score(validation_tar, predictions)
print('Val Accuracy = %.2f' % accuracy)
logging.info(('Val Accuracy = %.2f' % accuracy))
Storage.upload(tensorboard_logs,tensorboard_gcs_logs)
metadata = {'outputs': [{'type': 'tensorboard',
'source': tensorboard_gcs_logs,}]}
```

So, the preceding code contains the training and pre-processing with Image Data Generator after that we trained the model with preprocessed images in pipeline and the trained artifacts are saved as tensorflow models in GCP Bucket.

```
with open("/mlpipeline-ui-metadata.json", 'w') as f:
json.dump(metadata,f)
if mode!= 'local':
print("uploading to {0}".format(gcs_path))
Storage.upload(model_output_base_path,gcs_path)
else:
print("Model will not be uploaded")
pass
```

```
if __name__ == "__main__":
train_model()
```

So, the preceding code is the **train.py** file; lets break the pipeline code as follows: