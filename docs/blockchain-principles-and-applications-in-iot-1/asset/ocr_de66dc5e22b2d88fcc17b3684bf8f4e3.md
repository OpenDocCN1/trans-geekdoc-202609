# ASIC-Based Mining System in Blockchain

# 7.4.2.2 Problems with the UTXO Model in IoT

There are certain issues associated with using the UTXO model directly for IoT devices:

+   1. In a normal transaction, cryptocurrencies or other assets are sent from one account but for IoT devices, data will be recorded from sensors and hence it will need a different format. Unlike real-world transactions, there is no need for transaction verification or for double spend.
2. Since these transactions are selected from the transaction pool based on the transaction fees, there is a dependence on cryptocurrency for the system to run properly. IoT systems for smart cities will need a blockchain-based solution that can perform efficiently without any dependence on cryptocurrency.
3. If a transaction is not selected from the transaction pool for a long time, that particular transaction is dropped or marked as failed. This means there is an uncertainty that a transaction may fail even if it is valid. This may result in the loss of valuable data used in an IoT-based system. Here, there is a need for a mechanism that can guarantee every data is stored.

# 7.4.2.3 Proposed Model

The proposed model for storing IoT data has the following key differences:

+   1. Transaction Body: The transaction body will contain a unique transaction id and the sensor data as recorded from the sensor. The sensor will record data at a fixed time interval and create a transaction and pass the recorded data as a transaction body. Each represents represents newly recorded data, there is no to or from field. However, if a certain group of data needs role-based access control or encryption, then those too too be passed in the transaction body. There are no transaction fees involved and every transaction has the same priority.
2. Transaction Pool: When new data is recorded and a new transaction is created, that particular data is propagated to all other connecting nodes. Each node maintains a list of unconfirmed transactions. The list is maintained based on the timestamp of the recorded data in ascending order. If two different records have the same timestamp, they are stored in a queue in the order they receive.
3. Transaction Selection: The transactions will be selected from the pool of transactions based on timestamp. Since transactions are stored in the pool are also stored in ascending order of timestamp, this means the transactions will be selected in the same order as stored in the pool. The number of transactions that will be selected will depend on the number of transactions that can be stored in a block in proper order.

Since this model, transactions are selected in the order is recorded ensures that each transaction will definitely be mined. Since all transactions contain data from IoT devices, there is no need for a step similar to transaction validation which will reduce the processing time. Since the transactions are stored in UTXO format, an algorithm similar to the mining algorithm for Bitcoin can be used.