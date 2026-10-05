# 4.5 DECISION RULES

pre-mined conditions
Num.of.pregnancies=[3.67, 7.33]
UD=0, STDs=1
Number.of.sexual.partners=[1, 10),
STDs.Time.since.last.diagnosis=[1, 8]
First.sexual.intercourse=[10, 17.3), STDs=0
okes=1, IUD..years=[0, 6.33]
Hormonal.Contraceptives..years=[10, 20),
STDs..Number.of.diagnosis=[0, 1]
Age=[13, 36.7]
Hormonal.Contraceptives=1, STDs..Number.of.diagnosis=[0, 1]
Number.of.sexual.partners=[1, 10), STDs..number=[0, 1.33]
STDs..number=[1.33, 2.67), STDs..Time.since.first.diagnosis=[1,
8)

rules
If (yr=2011,temp=[-5.22,7.35]) (rule[718]) then positive
probability = 0.01014667
else (yr=2012,temp=[7.35,19.9]) (rule[823]) then positive
probability = 0.88125000
else (yr=2012,temp=[19.9,32.5]) (rule[816]) then positive
probability = 0.99253731
else (season=SPRING) (rule[351]) then positive probability =
0.06410256
else (temp=[7.35,19.9)) (rule[489]) then positive probability =
0.44444444
else (default rule) then positive probability = 0.79746835

for building a decision list. The maximum number of feature values in a condition I
allowed as a user two. Here is a sample of ten patterns:
Next, we use the SBRL algorithm to the bike rental prediction task. This only works if
t regression problem of predicting bike counts is converted into a binary classification task.
I have arbitrarily created a classification task by creating a label that is 1 if the number of
bikes exceeds 4000 bikes on a day, else 0.

The following list was learned by SBRL:
Let us predict that the number of bikes will exceed 4000 for a day in 2012
with a temperature of 17 degrees Celsius. The first rule does not apply, since it only applies
days in 2011. The second rule applies, because the day is in 2012 and 17 degrees lies in
the interval [7.35,19.9). Our prediction for the probability is that more than 4000 bikes
rented are 88%.