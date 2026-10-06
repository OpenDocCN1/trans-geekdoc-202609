# CHAPTER 24 CREATING LARGER ACTIVE DIRECTORY ENVIRONMENTS: BEYOND DOMAIN

The next page will display the option for Forest-wide Authentication or Selective Authentication. In many cases, you create a forest trust because you want all domains in one forest to trust all domains in the other forest. If that's the case, choose Forest-wide Authentication. If, on the other hand, you want to more finely tune the kind of authentication information that passes between the forests, then choose Selective Authentication. If you do, you'll have a lot more work ahead of you!

+   11. Click Next, and the wizard will ask you the same question from the point of view of the other forest.

+   12. Select whatever you prefer, and click Next Again.

You'll get two more information panels confirming what you've selected.

+   13. Click Next to get them past.

Then you'll be asked whether you want to confirm the link between forests. You'll end up at a final "This is what you did" page.

+   14. Click Finish, and it's done—Apex.com and Test.com are working as one, sort of.

Figure 24.24 shows the results on the Trusts tab. Apex.com is added in both fields. If you select to view the properties of a trust, you can run through the validation of the trust. This is useful in troubleshooting.

FIGURE 24.24
Trusts tab after the wizard

![](bbox=[0.318, 0.501, 0.682, 0.833])