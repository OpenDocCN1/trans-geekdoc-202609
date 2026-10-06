# CHAPTER 12 TRYING NOT TO MAKE A MESS: DATA COLLECTION AND STORAGE

different teams managing the data, like when analytics or data engineers are responsible for bringing the data into the standard locations that data scientists use. They often do some basic transformations and apply simple business rules to get the data ready to use.

These data teams should ensure basic quality of the data, such as making sure that unique keys are unique in the data, no duplicates are present, and there are no empty fields where not allowed. Data scientists generally shouldn't have concern themselves with this stuff, but the reality is that at a lot of companies, data engineers may not exist or may not do their diligence. So it's important for data scientists to be ready to check the quality of the data they're using unless they're extremely confident in the data engineers' work. This confidence usually comes after data has been used a lot and all the kinks have been worked out or when the data engineering team is very mature.

# Data and Information Organization

Although DBMSs ensure data is organized in certain ways, there are other ways of organizing data across multiple systems. There are a lot of terms floating around in this area, including data lakes, data warehouses, data silos, and data marts.

A silo is a collection of data that is locked down so areas and systems other than the intended users cannot access it. This often isn't an intentional thing—often data silos grow out of a particular area's needs. For instance, over time, HR has built up a lot of data that isn't shared outside of HR. But there may be parts of it that would be beneficial to other areas of the company without compromising privacy and compliance. Additionally, silos that have grown separately across different areas will have what is basically the same data stored in different silos, often in different forms. It may be exactly the same, which is inefficient and using unnecessary