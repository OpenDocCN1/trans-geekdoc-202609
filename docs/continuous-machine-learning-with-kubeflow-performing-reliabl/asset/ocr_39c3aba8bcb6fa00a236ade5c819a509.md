# 1.7 Optional: PVC setup for Jupyter Notebook

If you want to attach your PVC to the file store, so that you can save your data or codes in the Jupyter Notebook to external storage, then we can complete the following steps:

(Cost will be applied for 1TB storage)

Step Create a Filestore instance with 1 TB of storage capacity.

```
```bash
FS=[NAME FOR THE FILESTORE YOU WILL CREATE]
gcloud beta filestore instances create ${FS} \
--project=${PROJECT} \
--zone=${ZONE} \
--tier=STANDARD \
--file-share=name="volumes",capacity=1TB \
--network=name="default"
```
```

Step Retrieve the IP address of the Filestore instance.

```
```bash
FSADDR=$(gcloud beta filestore instances describe ${FS} \
--project=${PROJECT} \
--zone=${ZONE} \
--format="value(networks.ipAddresses[0])")
```
```