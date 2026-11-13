# Top tips!

# Criterion C

+   1 Testing strategies should be explicitly identified for each of your criteria for success. Functionally test and verify that your software functions according to requirements. Test that the range of inputs and outputs aligns with expected behaviour.
+   
+   2 Never trust the user! As discussed in A2.4.3, user inputs should always be validated before being used for any calculations or algorithms. Common validation methods for user inputs include:
+   - Presence check: Has a value been input?
+   - Length check: Is the input an acceptable length (minimum or maximum length)?
+   - Type check: Does the input correspond to the correct data types: integer, float, absence of illegal characters?
+   - Format check: Have any complex formatting rules been correctly applied (such as dates, times or currency)?

+   3 Validate your inputs by supplying expected and unexpected input values to test how your software responds. Normal data, boundary data and erroneous data inputs should all be tested. Remember that the guiding principle for assessment criteria in the Guide is:

> the system overview should have the clarity to enable a third party to re-create the product
> Does your response provide that level of clarity?

+   4 Recommended diagrams:
+   - Ul – mandatory
+   - ER (normalized) – if you have a database
+   - Data dictionary – if you have a database or persistent file storage
+   - UML diagram – if you are using OOP anywhere
+   - Component design diagram – if you have any physical hardware components
+   - Rules of engagement, attack surface mapping – if you have networking involved
+   - Flowcharting – for procedural code.

# Common mistakes

# Criterion C

+   1 A lack of design thinking being applied to your solution: if you have genuinely decomposed your problem scenario, there really shouldn’t be blocks of code hundreds of lines long (in criterion C, this could present as pseudocode that is overly long). This could be interpreted as a lack of effort to adequately think through and decompose your problem into abstractions such as classes or functions. The presence of variable names such as person1, person2, person3 may be interpreted as something that could have been better designed with an array.
+   
+   2 Avoid any technical errors in your diagrams (for example flowchart diagrams that have two arrows coming out of a non-decision element).
+   
+   3 Tests not actually relevant to achieving the proposed solution (likely linked to poorly devised success criteria): Things like “starts up within 10 seconds” or “does not crash”, instead of genuinely testing functionality, such as “successfully adds record to the XXX table of the database when a message is received”.