AI-Based Evaluation to assist Students Studying through Online Systems 159

Resets the Evaluator state to the Beginning
Args:

```
subject(str): Subject Name
"""
self._level = 1
self.subject = subject
```

```
def begin_course(self, subject):
    """
    Creates an Evaluator for the course
    Args:
        subject = Name of the Subject
```

```
self.subject = subject
self.evalator = Evaluator()
```

```
def answer_correctly_firstattempt(self, question):
    """
    Simulates the behaviour of the student responding with correct answer
in first attempt.\n    Args:
        question: Question for which the behaviour is observed and metrics collected
    Returns:
        metrics object of type Answer.
    """
```

```
metrics = Answer()
metrics.sample_answer_metrics(question, True, 1, True, 70.9)
return metrics
```

```
def answer_correctly_with_iteration(self, question):
    """
    Simulates the behaviour of the student responding with correct answer
with iteration.
    Args:
        question: Question for which the behaviour is observed and metrics collected
    Returns:
        metrics object of type Answer.
    """
```

```
metrics = Answer()
metrics.sample_answer_metrics(question, True, 1, False, 100)
return metrics
```

```
def answer_partly(self, question):
    """
```