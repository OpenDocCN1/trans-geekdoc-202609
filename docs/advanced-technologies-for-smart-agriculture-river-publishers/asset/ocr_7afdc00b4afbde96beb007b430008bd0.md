# Table 16.1 Various protocols applicable.

| Protocol | Latency | Bandwidth | Energy requirements | Reliability | Computational requirements | Data security |
|---|---|---|---|---|---|---|
| CoAP<br>MQTT<br>AMQP | Lowest<br>Low<br>Significantly lower | High<br>High<br>Significantly lower | High<br>High<br>Significantly lower | -<br>Best fit<br>- | Simple<br>Simple<br>- | DLS protocol<br>TLS protocol<br>SASL and TLS |
| Web Socket<br>XMPP | -<br>Significantly lower | -<br>Significantly lower | -<br>Significantly lower | -<br>- | -<br>- | TLS protocol<br>Built-in TLS |
| HTTP | - | - | - | Best fit | - | - |

# Table 16.2 Wireless technology used [8].

| Distance | Protocol | Network | Data rate | Frequency | Line of sight | Examples |
|---|---|---|---|---|---|---|
| Short-range applications | IEEE 802.15.4 | LPWAN | 20–250 kbps | 433 MHz, 868 MHz, 915 MHz, 2.4 GHz | 100 m | Bluetooth, RFID |
| Long-range applications | IEEE 802.11ah | LoRa/<br>LoRaWAN | 500 Mbps | 900 MHz | 1 Km | Cellular applications |