```
DNS-lookup: 0.0005 secs, 0.0000 secs, 0.0047 secs
req write: 0.0001 secs, 0.0000 secs, 0.0012 secs
resp wait: 2.4293 secs, 1.6787 secs, 3.0293 secs
resp read: 0.0000 secs, 0.0000 secs, 0.0001 secs

Status code distribution:
  [201] 200 responses
```

Once that has completed, if you refresh `localhost:4000/debug/vars` in your browser your metrics should now look something like this:

![](bbox=[0.125, 0.375, 0.875, 0.77])

Based on the `total_processing_time_us` and `total_responses_sent` values, we can calculate that the average processing time per request was approximately 2.4 seconds