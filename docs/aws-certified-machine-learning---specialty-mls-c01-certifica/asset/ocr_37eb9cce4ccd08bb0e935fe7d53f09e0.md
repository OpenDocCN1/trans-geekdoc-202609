3. There may be a situation where you have to roll back to the earlier version of the current object. In the preceding example, the latest one is Version-2. You can make any desired version the latest or current version by parsing the VersionId sub-resource to the get-object API call and uploading that object again. The other way is to delete the current or latest version by passing versionId to the –version-id parameter in the delete-object API request. More details about the API are available here: https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-object.html.

4. When you delete an object in a versioning-enabled bucket, it does not delete the object from the bucket. It just creates a marker called DeleteMarker. It looks like this:

```
$ aws s3api delete-object --bucket version-demo-mlpractice --key version-doc.txt
{
	"DeleteMarker": true,
	"VersionId": "BKv_Cxixtm7V48MWqBO_KUkKbcOaH5JP"
}
```

5. This means that the object is not deleted. You can list it by using this command: aws s3api list-object-versions --bucket version-demo-mlpractice

6. Now the bucket has no objects as version-doc.txt, and you can verify this using the aws s3 ls command because that marker became the current version of the object with a new ID. If you try to retrieve an object that is deleted, which means a delete marker is serving the current version of the object, then you will get a 404 error. Hence, the permanent deletion of an object in a versioning-enabled bucket can only be achieved by deleting the object using their version IDs against each version. If a situation arises to get the object back, then the same object can be retrieved by deleting the delete marker, VersionId, as shown in the following example commands. A simple delete request (without the version ID) will not delete the delete marker and create another delete marker with a unique version ID. So, it's possible to have multiple delete markers for the same object. It is important to note at this point that it will consume your storage and you will be billed for it:

```
$ aws s3 ls s3://version-demo-mlpractice/
$ aws s3api delete-object --bucket version-demo-mlpractice --key version-doc.txt --version-id BKv_Cxixtm7V48MWqBO_KUkKbcOaH5JP
{
	"DeleteMarker": true,
	"VersionId": "BKv_Cxixtm7V48MWqBO_KUkKbcOaH5JP"
}
```

7. Upon listing the bucket now, the older objects can be seen:

```
$ aws s3 ls s3://version-demo-mlpractice/
2020-11-07 15:57:05	10	version-doc.txt
```

As you have already covered the exam topics and practiced most of the required concepts, you should delete the objects in the bucket and then delete the bucket to save on costs. This step deletes the versions of the object and, in turn, removes the object permanently.

8. Here, the latest version is deleted by giving the version ID to it, followed by the other version ID:

```
$ aws s3api delete-object --bucket version-demo-mlpractice --key version-doc.txt --version-id 70wL6G6MBEQhQXmwsriDgQoXafFmgGi
$ aws s3api delete-object --bucket version-demo-mlpractice --key version-doc.txt --version-id fliC.9L.MsP0OtIb.sUMnfoOeAe240sIW
$ aws s3api list-object-versions --bucket version-demo-mlpractice
```

You can clearly see the empty bucket now.

# IMPORTANT NOTE