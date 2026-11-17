```
45. MDLabel:
46.     text: <Loan Amount>
47.     pos_hint: {<center_y>:0.54}
48.
49. MDTextField:
50.     id: input_4
51.     hint_text: <150>
52.     width: 100
53.     size_hint_x: None
54.     pos_hint: {<center_y>:0.54, <center_x>:0.50}
55.
56. MDLabel:
57.     text: <Credit History>
58.     pos_hint: {<center_y>:0.47}
59.
60. MDTextField:
61.     id: input_5
62.     hint_text: <0:Clear Debts, 1:Unclear Debts>
63.     width: 100
64.     size_hint_x: None
65.     pos_hint: {<center_y>:0.47, <center_x>:0.50}
66.
67. MDLabel:
68.     pos_hint: {<center_y>:0.2}
69.     halign: <center>
70.     text: <
71.     id: output_text
72.     theme_text_color: «Custom»
73.     text_color: 0, 1, 1, 1
74.
```