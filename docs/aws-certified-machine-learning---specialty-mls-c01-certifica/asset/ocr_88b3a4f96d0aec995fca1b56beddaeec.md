# Storing Data on Amazon S3

S3 is Amazon's cloud-based object storage service, and it can be accessed from anywhere via the internet. It is an ideal storage option for large datasets. It is region-based, as your data is stored in a particular region until you move the data to a different region. Your data will never leave that region until it is configured to do so. In a particular region, data is replicated in the availability zones of that region; this makes S3 regionally resilient. If any of the availability zones fail in a region, then other availability zones will serve your requests. S3 can be accessed via the AWS console UI, AWS CLI, AWS API requests, or via standard HTTP methods.

S3 has two main components: buckets and objects.

+   - Buckets are created in a specific AWS region. Buckets can contain objects but cannot contain other buckets.
+   - Objects have two main attributes. One is the key, and the other is the value. The value is the content being stored, and the key is the name. The maximum size of an object can be 5 TB. As per the Amazon S3 documentation (https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingObjects.html), objects also have a version ID, metadata, access control information, and sub-resources.

# IMPORTANT NOTE

As per Amazon's docs, S3 provides read-after-write consistency for PUTs of new objects, which means that if you upload a new object or create a new object and you immediately try to read the object using its key, then you get the exact data that you just uploaded. However, for overwrites and deletes, it behaves in an eventually consistent manner. This means that if you read an object straight after the delete or overwrite operation, then you may read an old copy or a stale version of the object. It takes some time to replicate the content of the object across three Availability Zones.

A folder structure can be maintained logically by using a prefix. Take an example where an image is uploaded into a bucket, bucket-name-example, with the prefix folder-name and the object name my-image.jpg. The entire structure looks like this: /bucket-name-example/folder-name/my-image.jpg.

The content of the object can be read by using the bucket name of bucket-name-example and the key of /folder-name/my-image.jpg.

There are several storage classes offered by Amazon for objects stored in S3:

+   - Standard Storage (S3 Standard): This is the storage class for frequently accessed objects and for quick access. S3 Standard has a millisecond first-byte latency and objects can be made publicly available.
+   - Standard Infrequent Access (S3 Standard-IA): This option is used when you need data to be returned quickly, but not for frequent access. The object size has to be a minimum of 128 KB. The minimum storage timeframe is 30 days. If the object is deleted before 30 days, you are still charged for 30 days. Standard-IA objects are resilient to the loss of Availability Zones.
+   - One Zone Infrequent Access (S3 One Zone-IA): Objects in this storage class are stored in just one Availability Zone, which makes it cheaper than Standard-IA. The minimum object size and storage timeframe are the same as Standard-IA. Objects from this storage class are less available and less resilient. This storage class is used when you have another copy, or if the data can be