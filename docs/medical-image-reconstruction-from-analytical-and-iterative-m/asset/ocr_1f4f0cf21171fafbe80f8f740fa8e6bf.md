is further decomposed into smaller segments (see Figure 9.28). We break down the bicycle template step by step. Eventually, the smallest templates can be as small as 3 × 3.

When we break down the pattern template to smaller templates, no fine details are lost. The earlier layers of the CNN are to catch the building components, and the later layers are to piece up the lower-level components to build a bicycle.

![](bbox=[0.1, 0.21, 0.52, 0.43])

Fig. 9.28: A small template of a bicycle is further broken down into much smaller templates of segments.

Here, we assume that the CNN has already been trained for bicycle detection and is ready to use. In a CNN, the procedure of identifying a bicycle is as follows. First, we find the cross-correlation images between the given big picture and all the lowest-level (with the finest details) templates. For any lowest-level template, a bright dot will show up in its associated layer output image when a match is found. The smaller cross-correlation values show up as black dots with a value 0 if there is no match, thanks to the nonlinear ReLU function and the bias at each cross-correlation unit (see Figure 9.29).

Some illustrative partial results are shown in Figures 9.29–9.31. The gray-color objects in these figures are not parts of the images or templates but are for location reference only.

After the first layer (see Figure 9.29), we know if the given picture contains the elements of arc segments.

After the second layer, one combination of the inputs (which are the outputs of the first layer units) matches the small template of the second layer. Hence, a circle is identified, and a bright dot shows up at the circle location in the associated output image of second layer. If there are two circles, two bright dots will appear at an output image of the second layer. Thus, a pair of side-by-side circles (i.e., the wheels) is identified. If no circle is identified, this cross-correlation will produce a black dot at the location, thanks to bias term and the nonlinear ReLU function attached to the end of the cross-correlation units.