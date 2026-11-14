```
$ ~/android/droidbox-read-only/DroidBox_4.1.1/droidbox.sh demo.apk
...
Waiting for the device...
Installing the application /home/demo/apk_samples/demo.apk...
Running the component
org.me.androidapplication1/org.me.androidapplication1.MoviePlayer...
Starting the activity .MoviePlayer...
Application started
Analyzing the application during infinite time seconds...
[\] Collected 10 sandbox logs  (Ctrl-C to view logs)
{
"apkName": "/home/demo/apk_samples/demo.apk", "enfperm": [], "recvnet": {},
"servicestart": {}, "sendsms": {"1.0308640003204346": {"message": "798657",
"type": "sms", "number": "3353"}, "1.1091651916503906": {"message": "798657",
"type": "sms", "number": "3354"}, "1.1251821517944336": {"message": "798657",
...}
}
```

After an arbitrary amount of time has passed, you can stop the monitoring by pressing CTRL-C, which will output logs in JavaScript Object Notation (JSON) format. The output in the previous listing was reduced for brevity. To format the JSON in a nicer way, use the following command:

```
$ cat droidbox.json | python -mjson.tool
...
```

```
...
"sendsms": {
	"1.0308640003204346": {
		"message": "798657",
		"number": "3353",
		"type": "sms"
	},
	"1.1091651916503906": {
		"message": "798657",
		"number": "3354",
		"type": "sms"
	},
	"1.1251821517944336": {
		"message": "798657",
		"number": "3353",
		"type": "sms"
	}
},
"servicestart": {}
}
```

From the output, it quickly becomes evident that the application is sending three SMS messages, as we have already discussed. The ability to observe and get insight into the application activity in such an easy way makes this approach very useful for malware-analysis purposes. It should be noted that this approach cannot be used by itself and has to