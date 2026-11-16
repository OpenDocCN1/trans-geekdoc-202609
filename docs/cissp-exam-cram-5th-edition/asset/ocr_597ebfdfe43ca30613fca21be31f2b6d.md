Some sources list only three goals of security by combining the third and fourth goals into one: maintain internal and external consistency and ensure that the data reflects the real world.

Two security models that address secure systems integrity include Biba and Clark-Wilson models, which are covered in the following sections. The Biba model addresses only the first integrity goal, and the Clark-Wilson model addresses all four goals.

# # Biba Model

The Biba model was the first model developed to address integrity concerns. Originally published in 1977, this lattice-based model has the following defining properties:

+   - **Simple integrity property**: This property states that a subject at one level of integrity is not permitted to read an object of lower integrity.
+   - **Star (*) integrity property**: This property states that an object at one level of integrity is not permitted to write to an object of higher integrity.
+   - **Invocation property**: This property prohibits a subject at one level of integrity from invoking a subject at a higher level of integrity.

> **Tip**
> 
> The star property in both the Biba and Bell-LaPadula models deals with writes. One easy way to remember these rules is to think, “It's written in the stars!”

The Biba model addresses only the first goal of integrity: protecting the system from access by unauthorized users. Other types of concerns such as confidentiality are not examined. This model also assumes that internal threats are being protected by good coding practices, and it therefore focuses