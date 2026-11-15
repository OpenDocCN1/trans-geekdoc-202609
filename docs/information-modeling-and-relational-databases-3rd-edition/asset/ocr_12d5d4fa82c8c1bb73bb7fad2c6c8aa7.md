![](bbox=[0.22, 0.1, 0.78, 0.39])

FIG. 14.44 This suboptimal schema maps to six tables.

+   - **Colecturing** ( topiccode_colecturer )<br>- **PGtopic** ( topiccode, topicTitle, headLecturer, period )<br>- **ActualPrerequisite** ( topiccode, actualPrereq )<br>- **PrefPrerequisite** ( topiccode, preferredPrereq )<br>- **TopicChoice** ( studentNr, subjectCode, topicCode )<br>- **Enrollment** ( studentNr, subjectCode )

FIG. 14.45 The relational schema mapped from Fig. 14.44.

PGtopic.topicCode (i.e., PGtopic.topicCode is the disjoint union of ActualPrerequisite.topicCode and PrefPrerequisite.topicCode). The ordinary “x” indicates that the topic-lecturer pairs in Colecturing and PGtopic are exclusive. The other constraints are straightforward.

Suppose a focused query for this domain is the following: list all topics (code and title) together with their main lecturers, co-lecturers, actual prerequisites, and preferred prerequisites. Let another focused query be the following: list students, the subjects in which they are enrolled, and the topics chosen by them (if any) for those subjects. With the relational schema of Fig. 14.45, the first query involves a join of four tables, and the second query involves a composite outer join of two tables. So, these queries will be slow to run.