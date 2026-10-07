# Scanning external repositories for keys

There are various commercial products available that monitor service account key leakage in public source repositories. We will look at an open source tool called Trufflehog that you can scan your private Git repository.

Truffhog is an open source tool you can use with git secrets. You can find it at https://packt.link/uoyAx. Trufflehog uses Shannon entropy to look through a repo's history for secrets. It does this by looking at the amount of entropy in the data.

Here is how you use Trufflehog:

```
trufflehog git https://github.com/repo/trufflehog-testing
```

The output looks like when it finds a service account key in the GitHub repo:

```
TruffleHog. Unearth your secrets. 
Found verified result 
Detector Type: GCP
Decoder Type: PLAIN
Raw result: svc-acct-key-test@test-project-1231232.iam.gserviceaccount.com
Repository: https://github.com/repo/repo
Timestamp: 2022-11-04 09:41:04 -0700 PDT
Line: 
Commit: 147d9de8555965f28f80cd45d1567c997b98e
File: sa-key.json
Email: jdoe <doe@acme.com>
Found unverified result 
Detector Type: PrivateKey
Decoder Type: PLAIN
```

As you can see, Trufflehog has found a private key in the Git repository. It also shows the email of the committer that committed the key.

So far, we have seen ways of managing security around service account keys. We will move on to understand a few more features of service accounts, such as how to create short-lived credentials.