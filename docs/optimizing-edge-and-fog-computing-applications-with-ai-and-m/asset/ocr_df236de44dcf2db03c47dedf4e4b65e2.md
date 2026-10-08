# ## 7.5 System Architecture of Federated Learning for Predictive Maintenance

The system architecture of Federated Learning for PdM consists of multiple components that work together to enable decentralized model training while preserving data privacy. This architecture ensures real-time monitoring, efficient local model updates, and global model aggregation without requiring raw data transmission.

# ### 7.5.1 Data Collection and Preprocessing

# #### 7.5.1.1 Data Collection

PdM relies on sensor-generated data from industrial machines, providing valuable insights into equipment health. These sensors continuously monitor parameters such as:

+   - **Temperature**—Detecting overheating components.
- **Vibration Levels**—Identifying mechanical imbalances.
- **Pressure**—Monitoring hydraulic or pneumatic systems.
- **Acoustic Signals**—Recognizing abnormal sounds in machinery.
- **Voltage and Current**—Detecting electrical faults.

Each device, such as an IoT gateway or industrial controller, collects data from these sensors in real time.

# #### 7.5.1.2 Data Preprocessing

Raw sensor data often contains noise, missing values, or inconsistencies due to sensor failures, environmental variations, or communication errors. Preprocessing ensures that the data is:

+   - **Cleaned**—Removing outliers and handling missing values.
- **Standardized**—Normalizing features to a common scale for consistent training.
- **Feature-engineered**—Extracting useful insights such as rolling averages, trend analysis, or frequency domain features using Fourier Transform.
- **Labeled** (if supervised learning is used)—Assigning failure or anomaly labels based on past maintenance records.

After preprocessed, the structured data is stored locally on edge devices for on-device training, eliminating the need for cloud storage of raw sensor data.