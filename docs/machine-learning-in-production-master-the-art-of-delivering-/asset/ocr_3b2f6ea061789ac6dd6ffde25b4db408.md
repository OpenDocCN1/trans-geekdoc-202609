```
14. self.lbl5.place(x=100, y=250)
15. self.t5.place(x=200, y=250, width=165)
17. self.b1=Button(win, text='Predict', command=self.predict, fg='blue')
18. self.b1.place(x=170, y=300)
20. self.lbl6.place(x=100, y=350)
21. self.t6.place(x=200, y=350)
```

Finally, define the **predict()** to make the prediction using the ML model based on user inputs.

```
1. # For making predictions
2. def predict(self):
3. self.t6.delete(0, 'end')
4. gender = float(self.t1.get())
5. married = float(self.t2.get())
6. income = float(self.t3.get())
7. loan_amt = float(self.t4.get())
8. credit_hist = float(self.t5.get())
9. prediction = model.predict([[gender, married, income, loan_amt, credit_hist]])[0]
10. if prediction == 0:
11. pred = 'Rejected'
12. else:
13. pred = 'Approved'
15. self.t6.insert(END, str(pred))
```