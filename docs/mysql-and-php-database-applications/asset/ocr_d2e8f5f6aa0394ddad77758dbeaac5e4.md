```
);
#
# Table structure for table 'substyles'
#
CREATE TABLE substyles (
  substyle_id int(11) NOT NULL auto_increment,
  category_id int(11) NOT NULL,
  substyle varchar(255) NOT NULL,
  price decimal(10,2),
  description text,
  PRIMARY KEY (substyle_id),
  KEY substyle_category_key (category_id)
);
#
# Table structure for table 'style_substyle_map'
#
CREATE TABLE style_substyle_map (
  style_id int(11) NOT NULL,
  substyle_id int(11) NOT NULL,
  price decimal(10,2),
  description text,
  image_src varchar(255),
  KEY map_style_key (style_id),
  KEY map_substyle_key (substyle_id)
);
```

# Code Overview

The code in this section is going to look substantially different from the chapters you have seen so far. Only the shopping cart (which, in fact, builds on this application) uses a similar method of organizing and accessing code. The other major differences are the use of utilities outside of PHP and accessing the file system.

# The object-oriented approach

In the preceding applications, and the ones that follow, we make use of a procedural approach. That is, there is a series of functions, and each function performs a fairly specific procedure. In the actual application, there is little to do but these functions. But in an application as this, where the data are largely hierarchical, it's helpful to make use of OO programming's inheritance. All a Style is really an extension of the process. The style may be red, but "red" means very little without the inherited property of t-shirt, which comes from the Category table.