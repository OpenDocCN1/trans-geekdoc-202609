
## AI-Based Evaluation to assist Students Studying through Online Systems

## TABLE 9.2
Static Attributes of a Question

| Attribute | Description |
| --- | --- |
| Identifier | To identify the question in a Programming Environment. |
| Content | Statement of the question (text, audio, video) |
| Type | Question type such as MCQ. Yes or No, etc. |
| List of Answer(s) Choices | Each element in the list has a set of choices to select the correct answer(s). If None, then the student needs to enter the answer. The list is provided to reframe the choices to Rule 7. |
| List of Correct Answer(s) | List of Correct Answer(s) corresponding to the List of Choices. |
| Number of Appearances | Maximum number of times a question is presented |
| Expected Answer Time Interval Between Appearances | Time required to answer by subject knowledgeable person The other options in the pool to be presented before this question can appear. The question will disappear at the end of this time. |

The dynamic attributes, given in Table 9.3, are updated after the student completes answering the question. The static attributes are referred (used) to select a question to be presented. Since we are not implementing the question delivery process, we shall force a question with minimal attributes to test our implementation.

## 9.7 EVALUATOR STATES AND ACTIONS

The Evaluator is implemented using a simple Markov Decision Process (MDP). The MDP States and the Actions are shown in Figure 9.2. It has five states: Beginning, Basic, Average, Good and Poor. The evaluator changes its state using present state, metrics collected from the student response to the question, and the student level.

Markov Decision Process Evaluators and the Actions are shown in Figure 9.2. The initial state of the Evaluator is S1 (Beginning). This state is assigned when the Evaluator is created to test a student on a new subject. The behaviour of the student, while answering the question, is observed and collected as metrics. They are listed below:

- 1. Answered
    a. Correct answer with first attempt
    b. Correct answer with iteration
    c. Partially correct answer
    d. Wrong answer
- 2. Not Answered

The logic used and the actions performed to implement the MDP uses these metrics. The State Transition Logic and the action taken is given below:

## Artificial Intelligence and Machine Learning in Business Management

## TABLE 9.3
Dynamic Attributes of a Question

| Name | Description | Remarks | Inference |
| --- | --- | --- | --- |
| Answer Time | Time taken to answer the question correctly | Stored as a List. This is a subset of list of response Time | The maximum time, minimum time (best answer time) and average time taken shall be calculated |
| Response Time | Total Time spent by the person | Stored as a List | It is possible to derive whether the visibility is time |
| Part Answer Time | Time taken to answer partly correctly | Stored as a List. This is a subset of list of response Time | |
| Number of correct answers | Number of persons answered correctly | | Larger number indicates that the question is easy |
| Number of wrong Answers | Number of persons answered wrongly | | Larger number indicates that the question is hard to solve or unclear |
| Number of partly correct answers | Number of persons answered partly correctly | Example: In MCQ, the correct answer could be more than one choice and the Person has selected a few and not a complete set. Not relevant for certain type of questions | Person lacks knowledge or insufficient time |
| Number of partly correct and partly wrong answers | Number of persons answered part correctly and part wrongly | Example: In MCQ, the correct answer could be more than one choice and the Person has selected a few correctly and few wrongly. Not relevant for certain type of questions | The person has not understood the subject completely. |
| Number of First Attempt of correct answer | Number of persons answered in first attempt, without correcting the answer before submitting the answer | This value will be less or equal to Persons correctly. The count excludes partly correct answers | The person is sure of the answer |
| Not Answered | Number of persons answered (may be due to timed out) | | Larger number indicates that the question is not clear and needs refraining |
| Current Appearance Number | A sequence number which gets incremented after every appearance | | Indicated the maturity level of the question and the evaluation outcome |

## AI-Based Evaluation to assist Students Studying through Online Systems 157

![](img/9665bc5b38d724f414bf1c78dda7410a_177_0.png)

**FIGURE 9.2** The MDP evaluator states and the actions.

- A. Answered
    a) If the question is answered correctly in the first attempt, both the State and student Level are incremented.
    b) If the question is answered correctly, but with iteration and if the Current State is not equal to the student level, then the State and student Level are decremented, else no change.
    c) If the question is answered part correctly, then the student Level is decremented.
    d) If the question is answered wrongly, then both the State and student Level are decremented.

- B. Not Answered
    a) If the question is not answered, then the State is decremented.

The state transition matrix is given in Table 9.4.
Assign Level 1 to a student when he/she starts to learn a particular subject. The progress of the student is measured periodically by conducting the evaluation process. The Student Level and the Evaluator State gets modified by the metrics collected while answering the question. In addition to this, the evaluation process provides feedback on the quality of the question. We have few more attributes, like Answer Time, Ratio of Correct and Wrong Answers, that could be used to improve the ML Process.

## TABLE 9.4
Evaluator State Matrix

| Behaviour | Current State | Next State | Student Level | Student Level |
|---|---|---|---|---|
| Correct Answer with first attempt | $S_i$ | $S_{i+1}$ | $L_i$ | $L_{i+1}$ |
| Correct Answer with iteration | $S_i$ | $S_{i-1}$ | $L_i$ | $L_{i-1}$ |
| Partly answer | $S_i$ | $S_i$ | $L_i$ | $L_{i-1}$ |
| Wrong Answer | $S_i$ | $S_{i-1}$ | $L_i$ | $L_{i-1}$ |

## Artificial Intelligence and Machine Learning in Business Management

## 9.8 IMPLEMENTATION

A sample evaluator process is written in Python 3.. Listing 1 has all the necessary Classes and Listing 2 is a test program to test the implementation.

### 9.8.1 LISTING 1

```python
# evaluator.py

class Student:
    def __init__(self, name):
        Initializer
        Args:
            name : Name of the Student

        self.level = 1
        self.name = name
        self.top_level = 4
        self.bottom_level = 0

    def reset(self, subject):
        """
        Resets the Evaluator state to the Beginning
        Args:
            subject(str): Subject Name
        """
        self._level = 1
        self.subject = subject

    def begin_course(self, subject):
        """
        Creates an Evaluator for the course
        Args:
            subject = Name of the Subject
        """
        self.subject = subject
        self.evalator = Evaluator()

    def answer_correctly_firstattempt(self, question):
        """
        Simulates the behaviour of the student responding with correct answer
in first attempt.
        Args:
            question: Question for which the behaviour is observed and metrics collected
        Returns:
            metrics object of type Answer.
        """
        metrics = Answer()
        metrics.sample_answer_metrics(question, True, 1, True, 70.9)
        return metrics

    def answer_correctly_with_iteration(self, question):
        """
        Simulates the behaviour of the student responding with correct answer
with iteration.
        Args:
            question: Question for which the behaviour is observed and metrics collected
        Returns:
            metrics object of type Answer.
        """
        metrics = Answer()
        metrics.sample_answer_metrics(question, True, 1, False, 100)
        return metrics

    def answer_partly(self, question):
        """
```
