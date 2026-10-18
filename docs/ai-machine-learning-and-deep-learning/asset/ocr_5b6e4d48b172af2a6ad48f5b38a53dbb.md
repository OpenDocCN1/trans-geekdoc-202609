Sample DT and DBSCAN constraints from PSCM and ADM are shown in [Table 18.4](#) and [Table 18.5](#).

# **Case Study 2**

We have also verified the performance of our proposed framework using real test bed data collected by the University of Queensland Vital Signs dataset [8]. The dataset collects 49 sensor measurements from more than 30 anesthesia patients undergoing surgery at Royal Adelaide Hospital and being monitored using Philips intellivue monitors and Datex-Ohmeda anesthesia machine. The preprocessed dataset possesses 209,115 samples with 26 sensor measurements and 58 patient status (labels) with 28 different alarms. Our attack analyzer found the feasibility of different attacks by raising wrong alarms instead of the intended ones. For instance, an adversary can activate alarms (APNEA, low blood pressure, low end-tidal carbon dioxide, high inspired concentration of sevoflurane) instead of other (APNEA, high minute volume) alarms by changing measurement values in artery diastolic pressure, artery mean pressure, effective end-tidal decreased hemoglobin oxygen saturation label, inspired decreased hemoglobin oxygen saturation label, end-tidal isoelectric point, inspired isoelectric point, effective end-tidal concentration of sevoflurane, and inspired concentration of sevoflurane sensors by 9%, 8%, 8.4%, 2.3%, 6%, 10%, 2%, 4%, respectively.

**TABLE 18.3** Attack Scenario Under Different Attack Models

| CURRENT STATE | HEART RATE | SYSTOLIC | DIASTOLIC | BLOOD OXYGEN |
|---|---:|---:|---:|---:|
| Actual measurements | 122.94 | 75.98 | 153.56 | 93/2 |
| Attacked measurements (DT constraints only) | 122.94 | 73.46 | 153.56 | 98.5 |
| Attacked measurements (both DT and DBSCAN constraints) | 120.332 | 81.855 | 149.67 | 98.5 |

**TABLE 18.4** Example of DT Algorithm-driven Constraints

**TABLE 18.5** Example of DBSCAN Algorithm-driven Constraints

# 18.5.2 Performance with Respect to Attacker Capability

The performance of our attack analyzer is primarily evaluated by enumerating the total identified attack vectors in terms of attacker’s capability. [Figure 18.7](#) demonstrates the total number of attack vectors found by our analyzers w.r.t. variable number of compromised sensor measurements and different thresholds for FDI attack in the case of a synthetic test bed. The attacker can attain an attack goal by compromising one sensor only as depicted from the figure. There are at most three possible attack vectors (when the attacker has the capability of compromising eight sensor measurements), provided the attacker is restricted to compromise the sensor measurements within the 10% threshold. The increment of threshold can figure out more attack vectors. For instance, our analyzer can identify 28 possible attack vectors, while it