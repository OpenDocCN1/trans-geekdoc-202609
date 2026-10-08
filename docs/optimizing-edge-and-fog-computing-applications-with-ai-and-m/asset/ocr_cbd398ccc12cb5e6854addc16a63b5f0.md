# Optimizing Edge and Fog Computing Applications with AI

![](bbox=[0.125, 0.116, 0.874, 0.388])

Figure 5.2 Virtual IoT devices on Node-RED.

+   - Log Pipeline: For a smooth and seamless transfer of data, filebeat is deployed and configured on the Suricata instance. It is used to store the logs from IDS to Logstash instance directly in real time. The Logstash processes and structures the data before sending and storing it in the Elasticsearch. This flow makes an efficient way to handle the data transmission.
- ELK stack SIEM: This is again deployed on a separate instance which is responsible for functioning of Elasticsearch, Logstash and Kibana. The main functionality of the SIEM here is to maintain the logs centrally which are received from the IDS, visualising the alerts triggered by the rule set in the Kibana and display it on the dashboards. It just inputs the data from IDS but also from the ML model instance further displaying its predictions.
- Trained models (EC2 instance): A separate and dedicated instance was deployed to store the trained models wherein it can fetch logs from Elasticsearch, classify them according to the trained models and index the predictions back to the Elasticsearch.
- Attacking Machine: While the above setup displays the detection capabilities, instance was deployed to generate the network traffic through simulation attacks. This is deployed on an isolated instance wherein a docker container is installed and used to simulate the DDoS attack using the hping3 command.



The detection mechanism used in this research uses a dual strategy wherein the detection relies on both rule-based detection using the SIEM capabilities and on the