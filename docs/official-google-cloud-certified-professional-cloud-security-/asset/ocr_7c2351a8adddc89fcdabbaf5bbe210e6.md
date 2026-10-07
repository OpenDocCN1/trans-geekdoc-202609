# Google Cloud Identity and Access Management

```
--format 'value (uniqueId)'
PRIVATE_KEY=$(openssl genrsa 2048)
```

2. Create a self-signed certificate:

```
openssl req -x509 -new \\n-key - \\n-subj /CN=customer@acme.com \\n-out csr.pem <<< $PRIVATE_KEY
```

```
openssl x509 \\n-in csr.pem \\n-signkey \\n-days 365 \\n-out certificate.pem <<< $PRIVATE_KEY
```

3. Upload the public part of the key to Google Cloud:

```
gcloud iam service-accounts keys \\nupload certificate.pem \\n-iam-account $SV_ACCT_EMAIL \\n-format json > uploaded.json\nPRIVATE_KEY_ID=$(jq -r .name uploaded.json | \\nawk -F'/' '{print $NF}')
```

4. Generate the service account key using the private part of the key. Look at the following code snippet:

```
touch look-no-keys.json\nchmod 0600 look-no-keys.json\njq -n \'\\n-arg PRIVATE_KEY "$PRIVATE_KEY" \\n-arg PROJECT_ID "$PROJECT_ID" \\n-arg SV_ACCT_EMAIL "$SV_ACCT_EMAIL" \\n-arg SV_ACCT_ID "$SV_ACCT_ID" \\n-arg PRIVATE_KEY_ID "$PRIVATE_KEY_ID" \\n'{\n  "type": "service_account",\n  "project_id": "$PROJECT_ID",\n  "private_key_id": "$PRIVATE_KEY_ID",\n  "private_key": "$PRIVATE_KEY",\n  "client_email": "$SV_ACCT_EMAIL",\n  "client_id": "$SV_ACCT_ID",\n  "auth_uri": "https://accounts.google.com/o/oauth2/auth",\n  "token_uri": "https://oauth2.googleapis.com/token"\n}
```