2. The following ORM schema models information about university academics. As a challenge exercise, map this to your preferred ER or IDEF1X notation, including some comments to cater for advanced constraints and multiple inheritance. You may wish to delay this until you have studied the relational mapping procedure in Chapter 11.

![](bbox=[0.13, 0.225, 0.84, 0.64])

*Each Teacher is an Academic who teaches some Subject.
*Each Professor is an Academic who has Rank ‘P’.
*Each TeachingProf is a Teacher and a Professor.

# 8.6 Summary

The ER modeling approach was originated by Peter Chen in the 1970s and allows facts to be expressed via relationships (e.g., Person was born in Country) or attributes (e.g., birthdate).

Of the dozens of different ER versions in existence, the most widely used are the Barker notation and IE. The popular IDEF1X approach is often referred to as a version of ER, but is actually a mixture of ER and relational approaches, with the emphasis on relational.

The Barker notation represents entity types as named, soft rectangles with a list of one or more attributes. A “*” or “•” indicates that an attribute is mandatory, and a “o” indicates