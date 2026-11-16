A rather obvious first step would be to apply the system to itself. In most applications, not everyone should be allowed to define or assign privileges. It makes good sense to create privileges for "View privileges", "Edit privileges" and "Delete privileges", as well as "Grant user privileges".

For complex applications with many different types of users, it would be helpful to build user types into the system. This would probably involve the addition of a `Usertype` table and a `UsertypePrivilege` table. In this way we can define which privileges will be available to which types of users. A data entry clerk may only be granted privileges concerning data entry, and a sales representative only privileges concerning sales. This would also affect the modifications described in the previous paragraph, as you would now need privileges such as "Grant data entry user privileges" and "Grant sales user privileges".

# # Summary

In this chapter we have looked at a case study of a user privilege system. During the course of this exercise we have touched on requirements, design patterns, multi-tier architecture, and the design process.

A multi-tier approach has many advantages over other design patterns, the most important of which is modularity. In our case study, changing the layout of the forms would not alter the design of the database abstraction layer as it is wholly independent. Using this approach in our case study has shown how simple and useful it can be.

The modularity of the user privilege system also allows it to be extended in many ways. Firstly, it could be applied to itself. Only certain people can set privileges for others, so they should be given a relevant privilege before they can access the system. Other extensions are also possible.