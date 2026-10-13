
![Fig. 7.31 The owns fact type is (a) asserted or (b) eagerly semiderived.](images/B978044323790400013X/f07-31-9780443237904.jpg)

[Fig. 7.31](#Ch007_273-308_B978044323790400013X.xhtml#B-f0160) The owns fact type is (a) asserted or (b) eagerly semiderived.

In [Fig. 7.31](#Ch007_273-308_B978044323790400013X.xhtml#f0160)(b), this feature is captured instead by the derivation rule: `^(++)Person owns Car if Person drives Car`. Some people might own a car but not drive it, so the ownership fact type must be at least partly asserted. The Person owns Car fact type is now semiderived. The `^(++)` superscript used here instead of the basic `^+` superscript for semiderivation indicates that the derived facts are to be stored immediately (*eager evaluation*).

From an implementation viewpoint, it is usually better to store the whole of the ownership relation under the control of the subset constraint or the eager semiderivation rule. This may take up a bit more storage, but access to ownership facts is fast.

From the *external* viewpoint, a user interface may be constructed to automatically add the required owner fact when a driver fact is added and to delete a driver fact when its owner fact is deleted. Such an interface could inform the user of its intended action and provide the option of canceling the transaction if this is not desired.

Apart from stored and derived redundancy, redundancy can occur within the set of derivation rules. For instance, it might be possible to derive a fact in more than one way, using different rules. Moreover, some rules might be derivable from more primitive rules. This situation is fairly common in formal inference systems (e.g., computer-aided reasoning systems).

In a wider context, redundancy can sometimes be very useful from the point of view of information retrieval, understanding (e.g., human communication), and coping with partial system failure (e.g., backup systems). This book itself exhibits a great deal of redundancy (e.g., by repeating important points). Although this makes the book longer, it hopefully makes it easier to follow.

The last check in the conceptual schema design procedure is to see if it is *complete* with respect to the original requirements specified for the application. This can be done systematically by going through each requirement, one at a time, and identifying which aspects of the conceptual design cater for it. If some requirements are found to be unfulfilled, the design should be extended to cater for them.

Apart from advanced aspects covered in [Chapter 10](#Ch010_401-479_B9780443237904000244.xhtml), this completes the conceptual schema design procedure. In terms of the application development life cycle, there are still several things to be done (e.g., mapping the conceptual design to a database schema; implementing physical and external schemas; testing; and maintenance). However, the most crucial stages of the cycle have now been considered. The final exercise question is a long one, covering most aspects of the CSDP.

## Exercise 7.5

1.  Discuss any problems with this schema (reference schemes are omitted for simplicity)

    ![](images/B978044323790400013X/u07-05-9780443237904.jpg)

2.  From the sample output report shown, a student draws the conceptual schema diagram shown. The elementary charge unit (e) is the electric charge of a single proton. Check to see if the data in the original report is a legal population of this schema. If not, modify the schema accordingly.

    ![](images/B978044323790400013X/u07-15-9780443237904.jpg)

    ![](images/B978044323790400013X/u07-06-9780443237904.jpg)

3.  Is this schema guilty of redundancy? If so, correct it.

    ![](images/B978044323790400013X/u07-07-9780443237904.jpg)

4.  With respect to the previous question, suppose it is now possible that bookshops in different cities have the same name. For example, the following population is legal. Draw the correct conceptual schema diagram for this UoD.

    ![](images/B978044323790400013X/u07-08-9780443237904.jpg)

5.  In Prolog, relations are often partly stored and partly derived. For example, at one state the knowledge base might consist of the following facts and rules. Discuss this situation making reference to the notion of derived redundancy.

    *   `parent_of(ann, bob).`
    *   `parent_of(bob, chris).`
    *   `grandparent_of(david, chris).`
    *   `grandparent_of(X, Y) if parent_of(X, Z) and parent_of(Z, Y).`

6.  An information system is to deal with various colors that are classified as primary (P), secondary (S), or tertiary (T). There are three primary colors: blue, red, and yellow. A secondary color is composed of a mixture of exactly two primary colors. A tertiary color is composed of exactly three primary colors.

    Each color has a unique, identifying trade name (e.g., "forest green"). The trade names of the primary colors are "blue", "red", and "yellow". Each color has a (perhaps zero) percentage of blue, red, and yellow. This percentage is expressed as a whole number in the range 0..100. For example, forest green is 70% blue and 30% yellow, but has no red. The following extract from a sample output report indicates the sort of information that needs to be accessed.

    ![](images/B978044323790400013X/u07-16-9780443237904.jpg)

    It is required to reduce the size of the database as much as possible by using derivation rules. For example, the percentage of a given color that is yellow should be derived from the percentages for blue and red. Schematize this UoD, indicating all constraints. State each derivation rule—you may use obvious abbreviations (e.g., `%B`, `%R`, and `%Y`). As long as circularity is avoided, the rule for computing the percent yellow may be assumed in formulating other rules (i.e., other rules may use the term `%Y`).

7.  An information system is required to manage data about various astronomical bodies in our solar system. The first table shows an extract from a report about moons. A "?" mark indicates unknown, and "–" indicates nonexistent.

    ![](images/B978044323790400013X/u07-17-9780443237904.jpg)

    Until a moon is given a normal name, it is assigned a temporary name based on the order in which the satellite was discovered for a given year and planet (do *not* bother unpacking these semantics). Here, "Explored" means the moon has been investigated by a spacecraft (manned or unmanned) from Earth. If a moon has an atmosphere, only its main gases are listed.

    If a moon has been explored, details about the missions to that moon may be recorded. A relevant extract of a report in this regard is shown in the next table. The meaning of bracketed contents in the mission entries in the first column needs to be made explicit. A "?" mark is a simple null (unknown) and a "−" mark indicates inapplicable because of other data.

    ![](images/B978044323790400013X/u07-18-9780443237904.jpg)

    Details of interesting features of various moons may be recorded. The next table shows a small extract of details from this record. Feature length measures are of only two types (diameter and linear).

    The type of a moon's feature does not determine its size type. For example, some grooved terrains might have a pencil-like shape and have their linear dimension measured, whereas other grooved terrains might have a roughly circular shape and have their diameter measured. Moreover, the size of a feature is recorded if and only if the size type of that feature is recorded.

    ![](images/B978044323790400013X/u07-19-9780443237904.jpg)

    The next table shows an extract of details about astronauts. The information system identifies astronauts by numbers to allow different astronauts with the same name and to track astronauts who change their names (ignore name tracking in your solution).

    ![](images/B978044323790400013X/u07-20-9780443237904.jpg)
