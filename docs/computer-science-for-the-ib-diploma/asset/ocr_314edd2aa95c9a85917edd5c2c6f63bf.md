# Python

```
class Assessment:
    def __init__(self, assessment_name, score):
        self._assessment_name = assessment_name
        self._score = score

    def get_score(self):
        return self._score

    def __str__(self):
        return f"{self._assessment_name}: {self._score}*"

class Student:
    _grade_boundaries = [80, 65, 50, 35, 20]
    _grades = ["A", "B", "C", "D", "E"]

    def __init__(self, student_name):
        self.student_name = student_name
        self._assessments = []
        self.current_grade = "N"  # Default to N before any grades are added

    def add_assessment(self, assessment):
        self._assessments.append(assessment)
        # Calculate new average
        average = self._get_average_score()
        # Update current grade
        self.current_grade = "N"  # Start with the default
        for i in range(0, len(Student._grade_boundaries)):
            if average >= Student._grade_boundaries[i]:
                self.current_grade = Student._grades[i]
                break

    def _get_average_score(self):
        if not self._assessments:
            return 0
        total = 0
        for assessment in self._assessments:
            total += assessment.get_score()
        return total / len(self._assessments)

    def __str__(self):
        return f"Student {self.student_name} has grade {self.current_grade}"

if __name__ == "__main__":
    student = Student("Doris")
    student.add_assessment(Assessment("Test 1", 75))
    student.add_assessment(Assessment("Homework", 85))
    student.add_assessment(Assessment("Exam", 65))
    print(student)
```