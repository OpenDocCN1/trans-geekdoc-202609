![](bbox=[0.14, 0.1, 0.75, 0.36])

Figure 13.9 A Detailed List of All Errors Appears

# 13.4 Prefill

We described the previous form check as "not constructive" a few pages earlier. This is still the case—detailed error message or not. Imagine if the form was a little longer and a user filled it out, which would certainly take five minutes. Unfortunately, the user forgot an important field. So he receives an error message and wants to fill in the missing field. But to his annoyance, the form is displayed *empty* again. In other words, the user has to fill all the fields in again.

On some (cheaper) websites, the developers take a very simple approach and ask the user to simply press the **Back** button in their web browser. Unfortunately, this does not always work as not all browsers cache all information; this also depends on the local settings, memory usage, and other general conditions.

The **Back** button approach is therefore not practical; on the contrary, it is out of the question. The only really feasible solution is to prefill the form with values that have already been entered.

Unfortunately, this approach has one disadvantage: it can sometimes be very laborious and time-consuming. This may well be the reason why it is left out of many books. However, it is a fact that this technique is required by clients and should be part of every PHP developer's toolkit. In our opinion, this topic should therefore not be omitted. And the tedious work of the following subsections has two advantages: First, the technique shown is always the same, so you can easily transfer it to your own forms. And second, you have a form that really helps the user to provide the required information—moving one more step toward a professional website.