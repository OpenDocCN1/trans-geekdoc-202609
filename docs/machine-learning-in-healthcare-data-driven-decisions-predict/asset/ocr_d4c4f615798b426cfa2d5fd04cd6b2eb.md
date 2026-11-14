As shown in Table 1, the literature points to a shift in the paradigm of healthcare to intelligent, patient-focused solutions. The solution developed in this study, which aims to solve entrenched issues like interoperability, security, and patient empowerment based on best practices and innovations outlined in the literature, draws from these developments. The suggested digital model strives to replicate a real-world, data-driven, patient-centric model that is future-proof, scalable, and resilient by bringing together knowledge from various lines of inquiry.

# 3 System Methodology: DigiCure Framework

In resource-limited environments, conventional health systems tend to be hampered by inefficiencies like faulty data, delayed diagnosis, and lack of patient participation. These inefficiencies lead to suboptimal care, delayed treatment, and wasteful healthcare expenditure. To address these inefficiencies, we present DigiCure, a simulation-driven digitalization platform that takes advantage of emerging technologies like telemedicine, IoMT, AI, and EHRs. The aim is to create an optimal, patient-focused health system with real-time monitoring, enhanced decision-making, and provider integration without a hitch.

# 3.1 Data Acquisition and Integration

The DigiCure system constructs an integrated digital health environment using a diverse set of data sources. The primary source of simulation is the MIMIC-III database, which contains over 53,000 patient records with diagnosis information, clinical measurements, and demographics. This set contains a wide range of measurements such as blood pressure, heart rate, temperature, test results, and medication history. IoMT streams are simulated for real-time monitoring of health and the MIMIC-III dataset. The IoMT sensors track vital parameters such as

+   - Heart rate: HR(t)
+   - Blood pressure: BP(t) = (Systolic(t), Diastolic(t))
+   - Temperature: T(t)

These IoMT devices stream continuous time-series data that is integrated with the AI models to monitor patient conditions dynamically. The AI model relies on both structured (e.g., lab tests and medications) and unstructured data (e.g., clinical notes) from the MIMIC-III database.

Real-time IoMT-derived vital signs and formatted clinical data from the MIMIC-III database are part of the simulated dataset employed in the DigiCure framework as illustrated in the tables. Essential patient parameters highlighted in Table 2 include