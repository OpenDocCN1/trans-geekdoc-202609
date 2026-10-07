# E Data Token Address

```
# Specify metadata & service attributes for Branin test dataset
# It's specified using local OOD data format: Aquarius will convert it to remote
# By using metadata and adding encrypted fields.
DATA_metadata = {
```

```
    "type": "dataset",
    "Files": [
        {
            "url": "https://github.com/tmcmc/branin/brainin.arrif",
            "Index": 0,
            "contenttype": "text/text",
            "name": "branin", "author": "Brent", "license": "CC0",
            "datecreated": "2019-12-20T10:55:12Z"
        }
    ]
}
```

```
DATA_service_attributes = {
```

# F Compute-to-job status

```
alice_service_index,
alice_job,
alice_wallet,
job_request.requirements=[]
```

```
job = compute.submit(
    dataset_id=dataset_id, data_id=data_id, service_index=service_index,
    job_request=job_request, bob_wallet=bob_wallet, alice_wallet=alice_wallet,
data_token_address=data_token_address
)
result = job.wait()
```

```
print(f"completed job with id: {job.id}")
completed job with id: 8154a53d-d551-4999-9229-4944a02d522d
```

# G Bob Downloads Data token

```
def func(task, **kwargs):
    # task downloads dataset
    dataset = kwargs.get('dataset')
    service = kwargs.get('service')
    data_token = kwargs.get('data_token')
    destination = kwargs.get('destination')
```

```
while True:
    # process data
    service_data = service.get_data(
        dataset_id=dataset_id,
        data_id=data_id,
        service_index=service_index,
        destination=destination
    )
```

![](bbox=[0.136, 0.815, 0.861, 0.933])