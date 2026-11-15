# Table 9.4 Extracted 153 features from mobile data

| Modality | Variables | Description |
|---|---|---|
| Survey | Same gender; age difference; is Facebook friend; frequency seen | Available from SNS and GPS |
| Profile features | Similarity of {last name, email domain, company name, phone number}; has {photo, ringtone, webpage, note, affiliation, work-phone & address, home-phone & address, email}; is starred; event type; completion of profile | Contact information |
| Call logs | Total {#, dur.} calls; total #lengthy-calls; | Intensity |
| | {AVG, SD, MIN, MAX, MED} #{outgoing, incoming} calls per week; #days called/days logged; {AVG, MAX} dur. {outgoing, incoming} calls | Regularity |
| | {#, dur.} outgoing calls/total calls; #{failed, missed} calls/outgoing (incoming) calls | Ch. selection and avoidance |
| | {#, dur.} calls at {times of a day, days of a week}/total calls; #{lengthy, failed, missed} calls at {times of a day, days of a week}/total (outgoing, incoming) calls | Temporal tendency |
| | {#, dur.} calls for the {past 2 weeks, past 3 months} / total calls | Maintenance cost |
| MSG logs | Total {#, length} MSGs | Intensity |
| | {AVG, SD, MIN, MAX, MED} #{outgoing, incoming} MSGs per week; #days MSGe/days logged; | Regularity |
| | {#, length} outgoing MSGs/total MSGs; #replied MSGs/total MSGs | Ch. selection and avoidance |
| | {#, length} MSGs at {times of a day, days of a week}/total MSGs | Temporal tendency |
| | {#, length} MSGs for the {past 2 weeks, past 3 months}/total MSGs | Maintenance cost |

We used four time segments and four day of the week segments: morning (6 am noon), afternoon (noon 6 pm), evening (6 pm midnight), and night (midnight 6 am); weekdays (Mon, Thu), Fri, Sat, and Sun. Note that “total” communication denotes all previous (logged) communications with the contact. COMM, communication; MSG, messages.