Two main points arising from this case study are: care is often required in choosing and identifying object types, and sample populations are not always significant. You are now invited to try your hand at a larger schema in the following exercise, which covers all aspects of the CSDP discussed so far.

# Exercise 5.4

+   1. The following reports are extracted from an information system used by an Australian tourism company. The first table provides details about tours offered by the company. Each tour must provide some kind of meal (snack or main meal).

| Tour | Tour Description | Snack | Main Meal | Duration (h) | Adult Fare (AUD) | Child Fare (AUD) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Gold Coast Grand Tour | | ✓ | 11 | 50 | 30 |
| 2 | Brisbane City Tour | ✓ | | 3 | 20 | 10 |
| 3 | Rainforest Tour | ✓ | ✓ | 10 | 40 | 22 |
| 4 | Quick Brisbane Tour | ✓ | | 1 | 5 | 2 |
| ... | ... | ... | ... | ... | ... | ... |

All tours are conducted on a daily basis. A tour may depart at more than one time. A given tour departing at a given time is called a “tour shift”. The next table shows an extract from the tour shift schedule. Details about a new tour, including its duration, may be recorded before shifts are assigned for that tour (e.g., no shifts have been decided yet for the Rainforest Tour). Each tour shift is offered in at least one language. A “?” mark denotes a null.

| Tour Shift | Language(s) supported | Tour | Departs | Returns | Driver Nr | Driver Name |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1A | English | 1 | 8:00 | 19:00 | 4 | Smith, John |
| 2A | English | 2 | 8:30 | 11:30 | 1 | Smith, John |
| 2B | Japanese | 2 | 10:00 | 13:00 | 3 | Kano, Fumie |
| 2C | English, Japanese | 2 | 14:00 | 17:00 | 1 | Smith, John |
| 4A | English, German | 4 | 8:00 | 9:00 | 3 | Kano, Fumie |
| 4B | English, Japanese, Spanish | 4 | 10:00 | 11:00 | ? | ? |
| 4C | French | 4 | 12:00 | 13:00 | 2 | Bell, Michelle |
| ... | ... | ... | ... | ... | ... | ... |

Details about tour drivers are maintained as shown below. Some drivers (e.g., driver 5) might not yet have been assigned to any tour shifts. A “?” mark denotes a null.