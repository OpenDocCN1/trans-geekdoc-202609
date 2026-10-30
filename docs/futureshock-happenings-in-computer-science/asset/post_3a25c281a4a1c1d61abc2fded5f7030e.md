
questions correctly, or participating in class discussions. Ideally, a point-based system could be integrated into a learning management system to provide immediate feedback, track progress, and even be exchanged for small rewards.

Badges serve as a form of recognition for achieving specific milestones or mastering particular skills. They can represent various achievements, such as completing a course module, demonstrating proficiency in a subject, or displaying good study habits. Badges provide a sense of accomplishment, but also allow students to showcase their achievements to peers, fostering a sense of community and friendly competition. Moreover, the collection of badges can encourage students to explore different learning paths and challenge themselves in new areas.

Leaderboards are another effective gamification tool that can boost motivation by introducing a competitive element to learning. By ranking students based on their performance or participation, leaderboards can create a sense of excitement. Courses at UNSW’s School of Computer Science and Engineering (CSE) such as Software Engineering Fundamentals have successfully utilised Leaderboards to anonymously rank students’ software accuracy. Anonymity, or pseudo-anonymity is essential to avoid discouraging lower-performing students. Leaderboards can be made more inclusive by recognising different types of achievements, such as effort or improvement, not just top scores. This approach ensures that all students feel motivated and valued, regardless of their initial skill level.

Gamification has been in many other domains, including gaming itself to motivate particular behaviours and engagement. The very popular video game Dota 2 uses various gamification elements including badges, points, and leaderboards, with the former depicted in Figure 3.7.

![](img/35d43ba1274e18d0f2f189e6392aa2e3_63_0.png)

Figure 3.7 The Popular DotA 2’s Badge System to Reward Player Progression

When thoughtfully integrated into the educational process, gamification elements like points, badges, and leaderboards can enhance student motivation, engagement, and overall learning outcomes.

## 3.6 ACADEMIC INTEGRITY AND MACHINE LEARNING

Recent developments in transformer-based machine learning (the technology which powers tools such as ChatGPT) has sent shockwaves into the assessment community. These systems can generate coherent, high-quality written content, making it easier for students to bypass the learning process and submit work that isn’t their own. Since the output is novel, existing plagiarism detection systems such as TurnItIn are not able to successfully detect the misconduct. This poses a serious problem: how can teachers assure that students engaged in learning activities, while operating at the scale of modern higher education? In this section, we look to how technology can help address the very problem it helped create.

### 3.6.1 LEARNING ANALYTICS

Learning analytics is an application of data science techniques, accounting for the idiosyncrasies of the educational landscape [15]. Learning analytics have many applications, from automatically detecting at-risk students, to gaining the knowledge required to be able to effectively optimise courses and training.

The first forward-looking application of learning analytics we will explore is academic misconduct detection. By analysing writing patterns, engagement, source material, and linguistic styles, machine-learning-based verification systems are tasked with identifying potential instances of misconduct, such as engaging with contract cheating services, or offloading assessments to generative AI.

There are two major approaches to detecting academic misconduct. The first is via keystroke logging and clickstream data, which attempts to detect irregularities in behaviour within the learning environment as students work on assessments over time [22]. The approach, while simple and effective, has two major criticisms. First, the approach relies on students developing their assessment (essay, code writing, etc) within a designated environment. This could prove inequitable for students who use third-party authoring tools, for example for accessibility purposes [19]. The second criticism of this approach is surrounding general privacy, with many students, educators and privacy advocates worried that online invigilated exams are a type of surveillance [10].

The second approach to detecting academic misconduct with learning analytics is via style detection. Style detection is the algorithmic validation of style over time [7, 5], and hinges on the idea that each individual has idiosyncrasies in their output. Most work in style validation is in writing style, but similar approaches are being explored in code writing and other domains. The approach, while more complex and prone to false positives [6], has clear benefits compared to behaviour logging as it is less important where the authorship of assessments took place, and no privacy-violating monitoring is required. The final product (be it an essay, source code, or any other written work) can simply be validated against previous examples of a student’s work.

These approaches offer a potential “way out” for the growing concern academics and educators have over the use of generative AI to produce novel works.

### 3.6.2 ONLINE INVIGILATION AND PSEUDO-INVIGILATION

The crammed lecture halls filled with nervous students hurriedly writing their final exams is a familiar picture for many around the world. In-person, invigilated examinations have served academic institutions for centuries, and for good reason— they offer high levels of assessment security. However, since the COVID-19 pandemic forced alternatives to in-person exams, Australian institutions are demonstrating reluctance in returning to in-person examinations. While there are many sound arguments in opposition of final exams for pedagogical purposes, it is clear that the high cost of running in-person exams is a key factor. Venue costs, staff costs, and materials all contribute to a relatively high cost for institutions to run examinations.

As institutions looked to alternative approaches to examinations during the COVID-19 pandemic, online proctoring or online invigilation technology promised the best of both worlds: invigilated examinations that students could take from their bedrooms.

Online, invigilated examination software such as Proctorio 3 and ProctorU4 were used extensively during pandemic-affected teaching periods. The tools work by constantly monitoring audio-visual feeds of the students’ environments during an exam, and have human invigilators or machine learning algorithms analyse the feeds to ensure a) the person in the feed matches the photo ID of the enrolled student, and b) that the student is not appearing to receive assistance from someone else online or in the room.

Many educators and academics expressed significant concern with these proctored systems, citing data privacy violations, biases and discrimination allegations. In one report, media site The Verge explores an investigation of online proctoring systems which falsely flag students of colour to academic misconduct teams because the machine learning algorithms cannot detect a human in the frame [3]

> > ‘You’re being watched and recorded, every breath’

As the dust has settled following the emergency response to COVID-19 teaching, it becomes clearer that the future of technologically-driven academic integrity will require privacy-friendly alternatives.

#### 3.6.2.1 Case Study: Real Talk with Deep Speaker

Due to the serious concerns with full-blown proctoring approaches, academics explored more student and privacy-friendly alternatives. One innovative approach to maintaining academic integrity is speaker verification. This technology utilises voice recognition to verify a student’s identity during oral examinations or assessments [18]. By ensuring that the student who registered for the course is the same person taking an online assessment, institutions can prevent impersonation and ensure that assessments reflect the student’s own understanding and abilities. This method is less intrusive than other forms of surveillance.

![](img/35d43ba1274e18d0f2f189e6392aa2e3_66_0.png)

Figure 3.8 The Deep Speaker System for Verifying Student Voice, as used in the Real Talk system [18]

The tool as developed and evaluated by [17], facilitated AI-invigilated oral assessments. Students were prompted to begin their online oral assessment by verifying that their microphone and speaker equipment was functional. Once ready, students were played back a pre-recorded audio question spoken by their teacher. The questions, while provided to all students for a particular assessment, asked questions specific to the student’s work. For example, “Can you explain, line by line, the code you wrote for assessment A”. Students then had to respond to the question in real time, with the AI system verifying the respondent’s identity. The study found that the tool was successful in delivering scalable oral assessments in large computing courses, and paints a picture for a future, privacy-friendly approach to high-stake assessments.

### 3.6.3 FUTURE ASSESSMENT SECURITY

Contract cheating and generative AI tools have created new challenges for maintaining academic integrity in higher education. Meanwhile, the very technology which threatened assessment offers promising solutions to these challenges. Learning analytics, including keystroke logging and style detection, provide ways to verify student work without invasive surveillance. Online invigilation systems, while controversial, offer alternatives to traditional in-person exams. Less intrusive methods like speaker verification present a balance between integrity and privacy concerns.

As the education industry moves forward, it’s clear that institutions have a variety of switches and levers which can be applied to design assessment of various levels of security and cost. More sophisticated and accurate style detection algorithms
