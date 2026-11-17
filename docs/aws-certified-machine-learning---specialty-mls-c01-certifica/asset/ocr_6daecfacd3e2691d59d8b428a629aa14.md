```
'HTTPHeaders': {'x-amzn-requestid': '74ca4afd-5844-47d8-9664-3660a26965e4', 'content-type': 'application/json', 'content-length': '471', 'date': 'Thu, 24 Sep 2020 18:50:57 GMT', 'RetryAttempts': 0},
'SynthesisTask': {'Engine': 'standard', 'TaskId': '57548c6b-d21a-4885-962f-450952569dc7', 'TaskStatus': 'scheduled', 'OutputUri': 'https://s3.us-east-1.amazonaws.com/polly-test-baba/output-audio/.57548c6b-d21a-4885-962f-450952569dc7.mp3',
'CreationTime': datetime.date(2020, 9, 24), 'RequestCharacters': 59, 'OutputFormat': 'mp3', 'TextType': 'text',
'VoiceId': 'Aditi', 'LanguageCode': 'en-GB'}})
```

The logs sample is shown in Figure 8.8:

| Log Entry | Details |
| :--- | :--- |
| > 2020-09-24T19:07:04.054+01:0... | Task Status is : scheduled |
| > 2020-09-24T19:07:04.094+01:0... | Task Status is : scheduled |
| > 2020-09-24T19:07:04.105+01:0... | Task Status is : scheduled |
| > 2020-09-24T19:07:04.184+01:0... | Task Status is : scheduled |
| > 2020-09-24T19:07:04.254+01:0... | Task Status is : inProgress |
| > 2020-09-24T19:07:04.497+01:0... | Task Status is : completed |
| > 2020-09-24T19:07:04.534+01:0... | Audio File Saved Successfully |
| > 2020-09-24T19:07:04.553+01:0... | END RequestId: 1d57151b-8462-434c-89b4-9b318c2437d8 |
| > 2020-09-24T19:07:04.553+01:0... | REPORT RequestId: 1d57151b-8462-434c-89b4-9b318c2437d8 Duration: 15832.73 ms Billed Duration: |
| | No newer events at this moment. Auto retry paused. Resume |

Figure 8.8 – The logs in the CloudWatch console

16. It will create output in MP3 format, as shown in Figure 8.9. Download and listen to it:

![](bbox=[0.265, 0.568, 0.733, 0.875])