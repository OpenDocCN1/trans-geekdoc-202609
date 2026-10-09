```
```json
"Properties": {
    "GroupDescription": "Enable SSH access",
    "VpcId": "vpc-09f1a480e4bd7aa6",
    "SecurityGroupIngress": [
        {
            "IpProtocol": "tcp",
            "FromPort": 22,
            "ToPort": 22,
            "CidrIp": "0.0.0.0/0"
        }
    ]
},
"Outputs": {
    "InstanceId": {
        "Description": "Instance ID of the newly created EC2 instance",
        "Value": {
            "Ref": "DeepLearningEC2Instance"
        }
    }
}
```
```

# ## Setting Up Amazon S3

Amazon Simple Storage Service (S3) is a highly scalable storage service offered by Amazon Web Services (AWS). Amazon S3 provides a reliable and cost-effective solution for storing and accessing large volumes of data. It offers high availability, durability, and scalability, making it an ideal