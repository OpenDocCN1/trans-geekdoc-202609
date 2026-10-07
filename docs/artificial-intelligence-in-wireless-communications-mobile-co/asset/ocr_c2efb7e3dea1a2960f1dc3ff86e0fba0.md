reads the XML format and builds a GNU Radio flow graph. [12] provides both the philosophy behind the use of XML for the interface language as well as the starting point to the waveform representation. The following XML shows a base representation for describing a GNU Radio transceiver. The description is split into a hierarchy that describes the transmit and receive independently, and under each of these are branches to describe different parts of the communications stack, such as the physical and link layers. The values of the knobs in a particular layer are then defined in the. It should be obvious how to add and define new knobs.

```
<?xml version="1.0" encoding="utf-8"?>
<waveform type="digital">
<Tx>
  <PHY>
    <rf>
      <tx_freq>408500000\<tx_freq>
      <tx_power>0.1\<tx_power>
    </rf>
    <mod>
      <tx_mod type="PSK">
        <tx_mod_bits>1\<tx_mod_bits>
        <tx_mod_differential>1\<tx_mod_differential>
      </tx_mod>
      <tx_rolloff>0.35\<tx_rolloff>
      <tx_bt>0.0\<tx_bt>
      <tx_gray_code>0\<tx_gray_code>
      <tx_symbol_rate>200000\<tx_symbol_rate>
    </mod>
  </PHY>
  <LINK>
    <frame>
      <tx_pkt_size>1450\<tx_pkt_size>
      <tx_access_code>0\<tx_access_code>
    </frame>
  </LINK>
</Tx>
<Rx>
  <PHY>
    <rf>
      <rx_freq>408500000\<rx_freq>
      <rx_gain>35\<rx_gain>
    </rf>
    <mod>
      <rx_mod type="PSK">
        <rx_mod_bits>1\<rx_mod_bits>
        <rx_mod_differential>1\<rx_mod_differential>
      </rx_mod>
      <rx_rolloff>0.35\<rx_rolloff>
      <rx_bt>0.0\<rx_bt>
      <rx_gray_code>0\<rx_gray_code>
      <rx_symbol_rate>200000\<rx_symbol_rate>
    </mod>
  </PHY>
</mod>
```