Garment transfer takes image of a person (target image) through the mobile camera and outputs person with overlayed costume.

# Wristwear try-on:

It mainly requires three components:

# Wrist tracking scene object:

The functionality of this object is to track the wrist. For this, wrist tracking custom component and wrist occluder is installed from the asset library.

# The left and right wrist objects:

It contains all the details related to the wrists.

# The 3D models:

These are the models for try-on.

The process follows the steps provided below:

+   1. Right click on the camera object in the left panel and select create scene object.
+   2. Rename the scene object as wrist tracking custom component.
+   3. Right click on the wrist tracking custom component and create two scene objects and rename them as left wrist and right wrist.
+   4. Click on the wrist tracking custom component scene object and click “+Add Component” in the inspector panel.
+   5. Add the wrist tracking to the scene object.
+   6. Click and drag left and right wrist scene objects from object panel to the inspector panel.
+   7. Click and drag Wrist_Occluder__PLACE_UNDER_WRIST_TRACKING_CC asset to the objects panel.
+   8. Make sure that Left Wrist Occluder is a child of Left wrist scene object and Right Wrist Occluder is a child of Right wrist.
+   9. Now import the 3D model in the object panels in the Left and Right wrists.
+   10. Adjust the positions, rotation, and scale of models in the inspector panel on the right.

Wristwear try-on takes person’s hand as input through the mobile camera and outputs a hand with overlayed watch.

# Footwear Try-On

It contains three main components: