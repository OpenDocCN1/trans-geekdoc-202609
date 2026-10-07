# Creating a symmetric key

To create a symmetric key, you will first need to create a key ring. The key ring determines the location of the key. Let us start with creating that.

# Step 1: Creating a key ring

Here is a gcloud kms keyrings command to create a key ring:

```
gcloud kms keyrings create key-ring-name \
  --location location
```

Replace key-ring-name with a name for the key ring to hold the key. Replace location with the Cloud KMS location for the key ring and its keys.

# Step 2: Creating a key

Use the following command to create a key in an existing key ring:

```
gcloud kms keys create key \
  --keyring key-ring-name \
  --location location \
  --purpose "encryption"
```

Replace key with the name of the key you would like to use and key-ring-name with the name of the key you created in the previous step. Replace location with the Cloud KMS location of the key ring. Note the *purpose* of this key.

# Step 3: Setting a key rotation period and starting time

Once the key is created, you can set a rotation period with a starting time. Here is the command that will allow you to do so:

```
gcloud kms keys create key \
  --keyring key-ring-name \
  --location location \
  --purpose "encryption" \
  --rotation-period rotation-period \
  --next-rotation-time next-rotation-time
```

Replace key with a name for the key. Replace key-ring-name with the name of the existing key ring where the key will be located. Replace location with the Cloud KMS location for the ring. Replace rotation-period with an interval such as 30d to rotate the key every 30 days. Replace next-rotation-time with a timestamp at which to begin the first rotation, such as 1970-01-01T01:02:03.