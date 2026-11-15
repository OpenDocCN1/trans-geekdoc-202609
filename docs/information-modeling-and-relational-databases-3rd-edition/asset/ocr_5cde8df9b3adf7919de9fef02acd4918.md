+   FormNr: 5001
+   
+   1. Age (years): .......
+   2. Nr hours spent per week watching TV: .......
+      If you answered 0 then go to Question 4
+   3. What is your favorite TV channel? .......
+   4. Nr hours spent per week reading newspapers: .......
+      If you answered 0 then Stop (no more answers are required).
+   5. What is your favorite newspaper? .......
+      If you are younger than 18, or answered 0 to question 2 or 4 then Stop (no more answers are required)
+   6. Which do you prefer as a news source?
+      (Check the box of your choice)
+      [ ] Television
+      [ ] Newspaper

FIG. 6.52 A sample media survey form.

As a simple example, consider the media survey form shown in Fig. 6.52. Each copy of the form has a unique form number. Each form is filled out by a different person, and each person fills out only one form. The enforcement of this 1:1 correspondence between people and forms is the responsibility of those conducting the survey rather than the information system itself. This correspondence is left implicit in the model, where people are identified directly by the form number.

The conditional instructions on this form are shown in italics. Everybody must answer questions 1, 2, and 4. Anybody who answers 0 to question 2 is told to skip question 3. Hence, favorite TV channel is recorded just for those who indicate they do watch some TV; let's call this subtype Viewer. People who answered 0 for question 4 are told to skip all later questions. Hence, favorite newspaper (question 5) is recorded just for those who read newspapers; let's call this subtype Reader.

People who are younger than 18 or are not both viewers and readers skip question 6. So, the preferred news source is recorded just for adult viewers who are also readers; let's call this subtype MediaAdult. This leads to the schema of Fig. 6.53.

Alternatively, an output report from the domain might help with the modeling (see Table 6.6). The sample data have been carefully chosen to be significant with respect to the subtype graph. Given this, and recalling that the “-” sign means “not to be recorded”, we may reason as follows. Age, viewing, and reading figures are recorded for everybody. The set of people for which favorite channel is recorded properly overlaps with the set of people for which favorite paper is recorded, so these correspond to overlapping subtypes. The set of people for which preferred news source is recorded is a proper subset of the previous two sets, so this corresponds to a common subtype.