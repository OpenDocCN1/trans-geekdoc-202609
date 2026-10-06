# Artificial Intelligence and Machine Learning in Business Management

studentD_evaluator.evaluate(studentD,metricsD)
metricsD = studentD.answer_correct_firstattempt(question4)
studentD_evaluator.evaluate(studentD,metricsD)
metricsD = studentD.answer_correct_with_iteration(question5)
studentD_evaluator.evaluate(studentD,metricsD)
metricsD = studentD.answer_correct_firstattempt(question6)
studentD_evaluator.evaluate(studentD,metricsC)
metricsD = studentD.answer_correct_with_iteration(question7)
performance_scoreD = studentD.evaluator.evaluate(studentD,metricsD)

# # Evaluate StudentE

```
print("Evaluating {} (StudentE)".format(studentE.name))
metricsE = studentE.did_not_answer(question1)
studentE_evaluator.evaluate(studentE,metrics_E)
metricsE = studentE.did_not_answer(question2)
studentE_evaluator.evaluate(studentE,metricsE)
metricsE = studentE.did_not_answer(question3)
studentE_evaluator.evaluate(studentE,metricsE)
metricsE = studentE.did_not_answer(question4)
studentE_evaluator.evaluate(studentE,metricsE)
metricsE = studentE.did_not_answer(question5)
studentE_evaluator.evaluate(studentE,metricsE)
metricsE = studentE.answer_correct_with_iteration(question6)
studentE_evaluator.evaluate(studentE,metricsE)
metricsE = studentE.answer_correct_firstattempt(question7)
studentE_evaluator.evaluate(studentE,metricsE)
metricsE = studentE.answer_correct_with_iteration(question8)
performance_scoreE = studentE.evaluator.evaluate(studentE,metricsE)
```

# # Evaluate StudentF

```
print("Evaluating {} (StudentF)".format(studentF.name))
metricsF = studentF.did_not_answer(question1)
studentF_evaluator.evaluate(studentF,metricsF)
metricsF = studentF.did_not_answer(question2)
studentF_evaluator.evaluate(studentF,metricsF)
metricsF = studentF.did_not_answer(question3)
studentF_evaluator.evaluate(studentF,metricsF)
metricsF = studentF.answer_correct_with_iteration(question4)
studentF_evaluator.evaluate(studentF,metricsF)
metricsF = studentF.answer_correct_with_iteration(question5)
studentF_evaluator.evaluate(studentF,metricsF)
metricsF = studentF.answer_correct_with_iteration(question6)
studentF_evaluator.evaluate(studentF,metricsF)
metricsF = studentF.answer_correct_firstattempt(question7)
studentF_evaluator.evaluate(studentF,metricsF)
metricsF = studentF.answer_correct_firstattempt(question8)
performance_scoreF = studentF.evaluator.evaluate(studentF,metricsF)
```