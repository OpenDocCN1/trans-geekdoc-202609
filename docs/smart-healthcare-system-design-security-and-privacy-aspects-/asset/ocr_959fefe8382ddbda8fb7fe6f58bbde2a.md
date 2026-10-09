SQL based database against the patient bed and patient id. The object based data such as the images, scanned documents etc. will be saved as objects in buckets in the public cloud infrastructure. Thus featuring a Hybrid Cloud System which shall ensure a high availability of information. The local private servers and the public cloud infrastructure will be in connection with AWS Direct Connect ensuring smooth and secure flow of information.

By this the doctors, medical health professionals and the nurses inside the local network of the institutions hold the capability to edit, write, and update the health records of the patients.

The body sensors which will be connected to any patient for diagnostic, treatment or health monitoring will be readly using a wireless area body network to send the data over to the nearest Raspberry Pi to which they are assigned to update and append the data tracked to the private dataserer present within the compound in sync with the cloud. The doctor, physicians or the emergency response teams can access patient's data directly from the local data server itself. Even if the stakeholders are not present within the compound they are able to login in to the cloud server to keep track of the medical record of the respective patient.

To ensure the security and privacy of the data that has been received from the body sensors on the patient, data transferred from the Raspberry Pi to the local server is encrypted. The encryption key is automatically managed by the local server itself which stores the ids for every Raspberry Pi for every specific bed. The data stored in the local servers are encrypted at rest. The data is analyzed using the cloud data lakes analytics using services like Amazon Redshift for a highly scalable data warehousing.

Further the stakeholders in the systems i.e. the medical health professionals, doctors, diagnostic centers, emergency health services such as ambulances and also authorized medical researchers can have access into the system.

# 7.3.1 Modules

# 7.3.1.1 Wireless Body Area Network

The wireless body area network is being proposed where the sensors are to be implemented in a hop star topology in the beacon modes where the network coordinator gets triggered up when the sensor nodes transmit any data. The standalone sensors such as the body temperature measuring and the ECG and respiration signal in real time sense the data and transmit