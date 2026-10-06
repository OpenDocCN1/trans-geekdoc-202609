# Al-Based Evaluation to assist Students Studying through Online Systems 163

first_attempt: Boolean. True for answered without iteration or False
answer_time: in Seconds
Returns:
Return the Performance score after evalauting the student
based on the input arguments.

```
if metrics.answered:
    if metrics.correct_answer == 1 and metrics.first_attempt:
        if self._state != self._upper_state:
            self._state += 1
        if student.level != student.top_level:
            student.level += 1
elif metrics.correct_answer == 1 and metrics.first_attempt== False:
    if student.level != self._lower_state:
        self._state -= 1
    if student.level != student.bottom_level:
        student.level -= 1
elif metrics.correct_answer == 0:
    if self._state != self._lower_state:
        self._state -= 1
    if student.level != student.bottom_level:
        student.level -= 1
else:
    if self._state != self._lower_state:
        self._state -= 1
```

```
# print("The Evaluator State is {} and the Student {} Level is {}").
# format(self._state, student.name, student.level))
return (self._state + student.level)
```

#End of Listing 1

# 9.8.2 LISTING 2

#testcases.py

from evaluator import *

#Create Seven Students and Register them for Algebra Class

studentA = Student('Anand')
studentA.begin_course('Algebra')