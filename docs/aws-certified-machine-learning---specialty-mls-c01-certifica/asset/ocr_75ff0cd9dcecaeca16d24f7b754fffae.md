5. If you want to upload your filesystem directories and files to the S3 bucket, then --recursive will do the job for you:

```
$ aws s3 cp . s3://demo-bucket-baba/ --recursive
upload: folder-1/a.txt to s3://demo-bucket-baba/folder-1/a.txt
upload: folder-2/sample-image.jpg to s3://demo-bucket-baba/folder-2/sample-image.jpg
upload: ./sample-file.txt to s3://demo-bucket-baba/sample-file.txt
$ aws s3 ls s3://demo-bucket-baba/
```

6. The contents of one bucket can be copied/moved to another bucket via the `cp` command and the `--recursive` parameter. To achieve this, you will have to create two buckets, `demo-bucket-baba-copied` and `demo-bucket-baba-moved`. The steps are as follows:

```
$ aws s3 mb s3://demo-bucket-baba-copied --region us-east-2
$ aws s3 mb s3://demo-bucket-baba-moved --region us-east-2
$ aws s3 cp s3://demo-bucket-baba s3://demo-bucket-baba-copied/ --recursive
$ aws s3 mv s3://demo-bucket-baba s3://demo-bucket-baba-moved/ --recursive
$ aws s3 ls
2020-11-04 14:39:50 demo-bucket-baba
2020-11-04 15:44:28 demo-bucket-baba-copied
2020-11-04 15:44:37 demo-bucket-baba-moved
$ aws s3 ls s3://demo-bucket-baba/
```

If all the commands are run successfully, then the original bucket should be empty at the end (as all the files have now been moved).

# NOTE

*In the certification exam, you will not find many questions on bucket- and object-level operations. However, it is always better to know the basic operations and the required steps.*

7. The buckets must be deleted to avoid costs as soon as the hands-on work is finished. The bucket has to be empty before you run the `rb` command:

```
$ aws s3 rb s3://demo-bucket-baba
$ aws s3 rb s3://demo-bucket-baba-moved
remove_bucket failed: s3://demo-bucket-baba-moved An error occurred (BucketNotEmpty) when calling the DeleteBucket operation: The bucket you tried to delete is not empty
```

8. The `demo-bucket-baba-moved` bucket is not empty, so you couldn’t remove the bucket. In such scenarios, use the `--force` parameter to delete the entire bucket and all its contents, as shown here:

```
$ aws s3 rb s3://demo-bucket-baba-moved --force
$ aws s3 rb s3://demo-bucket-baba-copied--force
```

If you want to delete all the content from a specific prefix inside a bucket using the CLI, then it is easy to use the `rm` command with the `--recursive` parameter.

9. Let’s take an example of a bucket, `test-bucket`, that has a prefix, `images`. This prefix contains four image files named `animal .jpg`, `draw-house .jpg`, `cat .jpg`, and `human .jpg`.

10. Now, to delete the contents inside the images, the command will be as follows: `aws s3 rm s3://test-bucket/images --recursive`

11. The bucket should now be empty.