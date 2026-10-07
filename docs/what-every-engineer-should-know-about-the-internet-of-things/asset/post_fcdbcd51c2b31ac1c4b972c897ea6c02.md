
# What Every Engineer Should Know About IoT

Machinery/Institute of Electrical and Electronic Engineers (ACM/IEEE) computer science knowledge areas (KAs). In addition, to highlight specific course projects, this chapter will be able to assist in the effort of building or adapting current academic programs offered to meet the current and future IoT/CPS development.

## 8.2 INTERNET OF THINGS

Since we are mapping the courses to the NIST NoT primitives discussed earlier in the book, a review of those primitives is useful. Recall that an IoT is representation of a NoT, and because of the upward trend of IoT applications and various domains, it is useful to use a consistent language to build NoTs (Voas, 2016). As described in Chapter 2, IoTs can be described by five primitives (i.e., the five Lego-like building blocks for any IoT-based system) as proposed in the NIST Special Publication 800-183 (Voas, 2016):

- 1. A sensor is an electronic utility (e.g., cameras and microphones) that measures properties such as sound, weight, humidity, temperature, and acceleration. Properties of a sensor could be the transmission of data or (e.g., RFID), Internet access, and/or be able to output data based on specific events.
- 2. A communication channel is the medium by which data is transmitted (e.g., via Universal Serial Bus (USB), wired, wireless, verbal). This software is based on mathematical functions.
- 3. An aggregator is software that can transform raw data (from any source) into intermediate, aggregated data. Aggregators have two actors for consolidating large volumes of data into lesser amounts:
- 4. Cluster is "abstract grouping of sensors (along with the data they output) can appear and disappear instantaneously"
- 5. Weight is the "degree to which a particular sensor will impact an aggregator's computation"
- 6. A decision trigger "creates the final result(s) needed to satisfy the purpose, specification and requirements of a specific NoT". A decision trigger is a conditional expression that triggers an action and absolutely defines the end purpose of a NoT. A decision trigger output can control actuators and transactions.
- 7. External utility (Utility) is a "hardware product, software or service that executes processes or feeds data into the overall data flow of the NoT"

Note, that any specifically proposed NoT may not include all five primitives. For example, you could have a NoT without any sensors. The simplest way to think about IoT is that the "things" are what make IoT unique. Remember, that the IoT is an acronym, the (T) is the letter that matters the most. The primitives are essentially the (T)s. We need to educate the next generation of computer scientists and engineers on the (T)s (DeFranco, Kassab & Voas, 2018).

## 8.3 THE ACM AND IEEE COMPUTER SCIENCE KNOWLEDGE AREAS

The ACM and IEEE Computer Society have a long record of sponsoring efforts to establish international curriculum guidelines for academic programs in computing. These guidelines are approximately a 10-year cycle starting with the publication of Curriculum 68 (Atchison et al., 1968) 50 years ago. The IEEE/ACM Curriculum Guidelines for Undergraduate Programs in Computer Science was published in 2013 (Force, 2013). In Computer Science, one can view the body of knowledge (BOK) as a specification of the content to be taught and a curriculum as an implementation. As shown in Table 8.1, the IEEE/ACM BOK is composed of 18 KAs.

KAs are not intended to be in one-to-one correspondence with a course that is part of a curriculum. A set of topics was recommended from Voas and Laplante to be considered when creating new computer science curricula, or the recommendations can be used to modify an existing computer science curriculum (Voas & Laplante, 2017). Further, if the curriculum is focused on CPS issues rather than IoT, modifying a systems engineering, electrical engineering, or mechanical engineering curricula might be worth pursuing as well.

## 8.4 MAPPING STUDY AND PROGRAMS REVIEW

We conducted a review with the goal of discovering how IoT knowledge is currently taught in academia. This review was completed in two parts:

- 1. Mapping Study: First we searched the Engineering Village database to learn about existing research and the proposed courses for designing and implementing IoT and CPS. The Engineering Village database is a comprehensive database that aggregates 12 engineering literature and patent databases to provide coverage from a wide range of trusted engineering sources.
- 2. Programs Review: In the second part of this review, we analyzed CPS and IoT-related programs at the top 50 universities ranked by Collegechoice.net and TopUniversities.com. Collegechoice.net is an aggregate of US News & World Report and the National Center for Education Statistics, and TopUniversities.com includes international universities for IoT and CPS courses.

### TABLE 8.1 IEEE/ACM Computer Science Knowledge Areas

| Algorithms and complexity | 10 | Networking and communications |
| :--- | :--- | :--- |
| Architecture and organization | 11 | Operating systems |
| Computational science | 12 | Platform-based development |
| Discrete structures | 13 | Parallel and distributed computing |
| Graphics and visualization | 14 | Programming languages |
| Human-computer interaction | 15 | Software development fundamentals |
| Information assurance and security | 16 | Software engineering |
| Information management | 17 | Systems fundamentals |
| Intelligent systems | 18 | Social issues and professional practice |

At this point, it is important to differentiate in order not to confuse "IoT in Education" and "IoT Education". IoT in Education was covered in another chapter of this book and focuses on technological tools that improve academic infrastructure. This discussion, IoT Education, focuses on courses or subjects which teach fundamental concepts of computer science (Elyamany & AlKhairi, 2015). An example of IoT Education is a focus on utilizing IoT in an education setting to manage student attendance with RFID readers at the school, library, cafeteria, dormitory entrances, and to monitor student activities (C2015). In this chapter, we are covering IoT Education. Thus, during the first part of the study, the research that focused on the first facet (IoT in education) were excluded.

While reading papers and reviewing the courses retrieved from the two parts of the study, the primitives and Computer Science KAs were documented. The findings are discussed in the next sections.

### 8.4.1 OVERVIEW OF COURSES FROM THE MAPPING STUDY

Nearly half of the courses discussed in the 11 identified are US based with others located in other countries (Italy, Spain, India, UK, and China).
