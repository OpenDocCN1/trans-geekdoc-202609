```
17. container_name: prometheus
18. ports:
19.   - 9090:9090
20. volumes:
21.   - ./prometheus.yml:/etc/prometheus/prometheus.yml
22. command:
23.   - "--config.file=/etc/prometheus/prometheus.yml"
24. networks:
25.   example-network:
26.     ipv4_address: 172.16.238.11
27.
28. grafana:
29. image: grafana/grafana:latest
30. restart: unless-stopped
31. user: "472"
32. container_name: grafana
33. depends_on:
34.   - prometheus
35. ports:
36.   - 3000:3000
37. volumes:
38.   - ./datasource.yml:/etc/grafana/provisioning/datasource.yml
39. env_file:
40.   - ./config.monitoring
41. networks:
42.   example-network:
43.     ipv4_address: 172.16.238.12
44.
45. networks:
46.   example-network:
47.     # name: example-network
```