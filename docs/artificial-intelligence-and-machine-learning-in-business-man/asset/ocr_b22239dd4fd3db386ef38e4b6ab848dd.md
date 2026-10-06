# AI-Based Evaluation to assist Students Studying through Online Systems 153

+   - Environment:
It is the context in which the agent performs. It consists of State, Dynamics and Rewards.
State represents all possible existence of the environment. The Agent steps the environment through the states as per the current situation.
Dynamics describe how actions influence the state of the environment.
Rewards describe the agents' goal or environmental feedback.
- Policy describes the behaviour of the agent. Agent selects by following the policies.

We shall now map these elements to our problem.

The Agent we will detail is the Evaluation Mechanism. In the online learning environment, we have more agents like content delivery, question Generation etc. Actions for the Evaluation Process are:

+   - Selecting a question
- Performing the test
- Collect metrics
- Analyse the metrics
- Update the student level
- Update the question attributes

For the implementation, we shall focus on Analyzing the Metrics, Updating the student level and Updating the question Attributes. Environment consists of

+   - Question and its attributes
- Student Levels (Grades)
- Poor or Cannot Grade (Level 0)
- Beginner (Level 1)
- Average (Level 2)
- Good (Level 3)
- Excellent (Level 4)
- Environment State (Beginning, Basic, Average, Good and Poor)
- Rewards for the question (derived from the feedback by the evaluation process)
- Rewards for the content delivery (derived from the feedback by the evaluation process)

# Policy:

The logic used by the agent to perform. The logic is built from the attributes of the question, student response metrics and Current Level of the Student. The policies are required:

+   - To select the question
- To measure the student level
- To update the attributes of the question