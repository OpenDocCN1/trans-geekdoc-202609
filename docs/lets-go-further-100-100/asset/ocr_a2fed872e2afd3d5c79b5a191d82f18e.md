+   - The average number of requests received per second (between calls A and B to the `GET /debug/vars` endpoint):
+   - The average processing time per request (between calls A and B to the `GET /debug/vars` endpoint):

```
(total_requests_received_B - total_requests_received_A) / (timestamp_B - timestamp_A)
```

```
(total_processing_time_us_B - total_processing_time_us_A) /
(total_requests_received_B - total_requests_received_A)
```